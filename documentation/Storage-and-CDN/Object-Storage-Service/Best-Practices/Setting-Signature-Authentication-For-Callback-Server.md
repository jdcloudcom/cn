# 回调服务器设置签名认证

## 概述
如果您的回调服务器被人恶意攻击了，例如恶意回调您的应用服务器，导致应用服务器收到一些非法的请求，影响正常逻辑，此时您就需要判断回调请求是否来自OSS。

在OSS回调通知及视频回调中，通知消息通过NS服务发到您的回调服务器。NS支持签名认证，具体方法如下：

## 验证回调签名
用户可以通过推送请求Header中的 x-jdcloud-signing-cert-url 获取签名证书，并根据相应的方法来验证该请求是否由NS系统发出，防止恶意请求对用户造成负面影响。

在 NS 推送请求的 Header 中，Authorization 字段的值是MNS根据待签名字符串，用 SHA1-RSA 签名算法生成签名。Endpoint 可以使用公钥对签名进行验证，具体的验证方法如下：

### 第一步：获取X509证书

在 NS 发送给 Endpoint 的 http 请求 Header 中，x-jdcloud-signing-cert-url 指定了签名证书的地址（ Base64 编码），用户需要通过 Base64 解码，获取该签名文件 URL 地址，再从中提取出签名的公钥。

### 第二步：计算待签名字符串
```
 VERB + "\n"
+ CONTENT-MD5 + "\n"
+ CONTENT-TYPE + "\n"
+ DATE + "\n"
+ CanonicalizedNSHeaders
+ CanonicalizedResource
```
注：
* VERB 表示HTTP的Method
* CONTENT-MD5 表示请求内容数据的MD5值
* CONTENT-TYPE 表示请求内容的类型，对应的值为全小写
* DATE 表示此次操作的时间，不能为空，目前只支持GMT格式
* CanonicalizedNSHeaders 表示 http 请求 Header 中的x-jdcloud-开始的字段组合（见下文注意事项）
* CanonicalizedResource 表示 http 请求的相对地址，不能为空
待签名字符串示例（注：不应该出现空的行全小写，Content-Type值为全小写）：
```
POST
ZDgxNjY5ZjFlMDQ5MGM0YWMwMWE5ODlmZDVlYmQxYjI=
text/xml;charset=utf-8
Wed, 25 May 2016 10:46:14 GMT
x-jdcloud-request-id:57458276F0E3D56D7C00054B
x-jdcloud-signing-cert-url:aHR0cDovL25zdGVzdC5vc3MuY24tbm9ydGgtMS5qY2xvdWRjcy5jb20veDUwOV9wdWJsaWNfY2VydGlmaWNhdGUucGVtCg==
x-jdcloud-version:2015-06-06
/notifications
```
### 第三步：Authorization 解密
对Authorization 签名字段进行 Base64 Decode 解码后，使用从第一步从证书中提取的公钥对其进行解密；
### 第四步：认证
比较第二步生成的待签名字符串与第三步解密的结果是否一致。如果一致，则表明请求来自NS，访问合法。
注：
* CanonicalizedNSHeaders（即x-jdcloud-开头的head）在签名验证前需要符合以下规范:
* head 的名字需要变成小写
* head 自小到大排序
* 分割 head name 和 value 的冒号前后不能有空格
* 每个Head之后都有一个\n，如果没有以x-jdcloud-开头的head，则在签名时CanonicalizedNSHeaders就设置为空

### 其他
1.用来签名的字符串为 UTF-8 格式;

2.签名的方法用 RFC 3447 ( http://tools.ietf.org/html/rfc3447 )中定义的 sha1WithRSAEncryption 方法;

3.Base64 是指使用 base64 算法转码文本

### Java示例代码
```
ublic class SignDemo {
      private Boolean authenticate(String method, String uri, Map<String, String> headers) {
          try {
              //获取证书的URL
              if (!headers.containsKey("x-jdcloud-signing-cert-url")) {
                  System.out.println("x-jdcloud-signing-cert-url Header not found");
                  return false;
              }
             String cert = headers.get("x-jdcloud-signing-cert-url");
             if (cert.isEmpty()) {
                 System.out.println("x-jdcloud-signing-cert-url empty");
                 return false;
             }
             cert = new String(Base64.decodeBase64(cert));
             System.out.println("x-jdcloud-signing-cert-url:\t" + cert);
  
             //根据URL获取证书，并从证书中获取公钥
             URL url = new URL(cert);
             HttpURLConnection conn = (HttpURLConnection) url.openConnection();
             DataInputStream in = new DataInputStream(conn.getInputStream());
             CertificateFactory cf = CertificateFactory.getInstance("X.509");
             Certificate c = cf.generateCertificate(in);
             PublicKey pk = c.getPublicKey();
  
             //获取待签名字符串
             String str2sign = getSignStr(method, uri, headers);
             System.out.println("String2Sign:\t" + str2sign);
  
             //对Authorization字段做Base64解码
             String signature = headers.get("Authorization");
             byte[] decodedSign = Base64.decodeBase64(signature);
  
             //认证
             java.security.Signature signetcheck = java.security.Signature.getInstance("SHA1withRSA");
             signetcheck.initVerify(pk);
             signetcheck.update(str2sign.getBytes());
             Boolean res = signetcheck.verify(decodedSign);
             return res;
         } catch (Exception e) {
             e.printStackTrace();
             return false;
         }
     }
  
     private String getSignStr(String method, String uri, Map<String, String> headers) {
         StringBuilder sb = new StringBuilder();
         sb.append(method);
         sb.append("\n");
         sb.append(safeGetHeader(headers, "Content-md5"));
         sb.append("\n");
         sb.append(safeGetHeader(headers, "Content-Type"));
         sb.append("\n");
         sb.append(safeGetHeader(headers, "Date"));
         sb.append("\n");
  
         List<String> tmp = new ArrayList<String>();
         for (Map.Entry<String, String> entry : headers.entrySet()) {
             if (entry.getKey().startsWith("x-jdcloud-")) {
                 tmp.add(entry.getKey() + ":" + entry.getValue());
             }
         }
         Collections.sort(tmp);
  
         for (String kv : tmp) {
             sb.append(kv);
             sb.append("\n");
         }
  
         sb.append(uri);
         return sb.toString();
     }
  
     private String safeGetHeader(Map<String, String> headers, String name) {
         if (headers.containsKey(name)) {
             return headers.get(name);
         } else {
             return "";
         }
     }
  
     public static void main(String[] args) {
         SignDemo sd = new SignDemo();
         Map<String, String> headers = new HashMap<String, String>();
         headers.put("Authorization", "Mko2Azg9fhCw8qR6G7AeAFMyzjO9qn7LDA5/t9E+6X5XURXTqBUuhpK+K55UNhrnlE2UdDkRrwDxsaDP5ajQdg==");
         headers.put("Content-md5", "M2ViOTE2ZDEyOTlkODBjMjVkNzM4YjNhNWI3ZWQ1M2E=");
         headers.put("Content-Type", "text/xml;charset=utf-8");
         headers.put("Date", "Tue, 23 Feb 2016 09:41:06 GMT");
         headers.put("x-jdcloud-request-id", "56CC2932F0E3D5BD530685CB");
         headers.put("x-jdcloud-signing-cert-url", "aHR0cDovL25zdGVzdC5vc3MuY24tbm9ydGgtMS5qY2xvdWRjcy5jb20veDUwOV9wdWJsaWNfY2VydGlmaWNhdGUucGVtCg==");
         Boolean res = sd.authenticate("POST", "/notifications", headers);
         System.out.println("Authenticate result:" + res);
     }
 }
```
