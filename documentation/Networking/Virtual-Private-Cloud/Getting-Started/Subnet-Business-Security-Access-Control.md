## **����ҵ��ȫ���ʿ���**

### **����**

ͨ���˽�ѧ�������ھ�����������ɻ���������ģ�Ͳ���һ����������WEB��һ�������߼���APP��һ���������ݵ�DB�㡣����WEB��ֻ���빫����APP�㻥ͨ��APP��ֻ����WEB���DB�㻥ͨ��DB��ֻ����APP�㻥ͨ����ɺ�ɻ��������Դ��

- 1��˽������
- 3������
- 3��ACL



### **��������**

#### **��һ��������˽������**

- ��������͵������ε������->˽������->˽�����磬����˽�������б�ҳ����������������������ô��ڡ�
- ��������ѡ��ĵ�����д���ƣ���дCIDR������������ɻ��1��˽�����硣
- ���̳��н���˽�������CIDR����Ϊ10.0.0.0/16��

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step1.png)



#### **�ڶ�������������WEB�㡢APP�㡢DB������**

- ��������͵������ε������->˽������->���������������б�ҳ����������������������ô��ڡ�
- ��������ѡ��ĵ���ѡ��ոմ�����˽�����磬��д�������ƣ���д����CIDR��ѡ�����·�ɱ�����������ɡ��ظ����鼴�ɻ��3��������
- ���̳��н�WEB������CIDR����Ϊ10.0.1.0/24��APP������CIDR����Ϊ10.0.1.0/24��DB������CIDR����Ϊ10.0.2.0/24��

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step2.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step2-2.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step2-3.png)



#### **�����������ò���ACL**

##### ����ACL

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-1.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-2.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-3.png)



##### **WEB��ACL����**

##### ������վ����

- ����WEB����APP��֮����վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��ԴIP��Ϊ10.0.1.0/24��������Ϊ���ܡ�
- ����WEB�����VPC����������֮����վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��ԴIP��Ϊ10.0.0.0/16��������Ϊ�ܾ���
- ����WEB���빫��֮����վ������򣬽����ȼ���Ϊ20000��������ΪALL traffic��ԴIP��Ϊ0.0.0.0/0��������Ϊ���ܡ�

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-4.png)



##### ���ó�վ����

- ����WEB����APP��֮���վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��Ŀ��IP��Ϊ10.0.1.0/24��������Ϊ���ܡ�
- ����WEB�����VPC����������֮���վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��Ŀ��IP��Ϊ10.0.0.0/16��������Ϊ�ܾ���
- ����WEB���빫��֮���վ������򣬽����ȼ���Ϊ20000��������ΪALL traffic��Ŀ��IP��Ϊ0.0.0.0/0��������Ϊ���ܡ�

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-5.png)



#### **���ù�������**

- �����������TAB->����������ť���򿪹����������õ�����
- ѡ��WEB�����������ȷ��������á�

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-6.png)



#### **APP��ACL����**

##### ������վ����

- ����APP����WEB��֮����վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��ԴIP��Ϊ10.0.0.0/24��������Ϊ���ܡ�
- ����APP����DB��֮����վ������򣬽����ȼ���Ϊ300��������ΪALL traffic��ԴIP��Ϊ10.0.2.0/24��������Ϊ���ܡ�
- ����APP�����VPC����������֮����վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��ԴIP��Ϊ10.0.0.0/16��������Ϊ�ܾ���

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-7.png)



##### ���ó�վ����

- ����APP����WEB��֮���վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��Ŀ��IP��Ϊ10.0.0.0/24��������Ϊ���ܡ�
- ����APP����DB��֮���վ������򣬽����ȼ���Ϊ300��������ΪALL traffic��Ŀ��IP��Ϊ10.0.2.0/24��������Ϊ���ܡ�
- ����APP�����VPC����������֮���վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��Ŀ��IP��Ϊ10.0.0.0/16��������Ϊ�ܾ���

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-8.png)



#### **���ù�������**

- �����������TAB->����������ť���򿪹����������õ�����
- ѡ��APP�����������ȷ��������á�

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-9.png)



#### **DB��ACL����**

##### ������վ����

- ����DB����APP��֮����վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��ԴIP��Ϊ10.0.1.0/24��������Ϊ���ܡ�
- ����DB�����VPC����������֮����վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��ԴIP��Ϊ10.0.0.0/16��������Ϊ�ܾ���

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-10.png)



##### ���ó�վ����

- ����DB����APP��֮���վ������򣬽����ȼ���Ϊ200��������ΪALL traffic��Ŀ��IP��Ϊ10.0.1.0/24��������Ϊ���ܡ�
- ����DB�����VPC����������֮���վ�ܾ����򣬽����ȼ���Ϊ10000��������ΪALL traffic��Ŀ��IP��Ϊ10.0.0.0/16��������Ϊ�ܾ���

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-11.png)



#### **���ù�������**

- �����������TAB->����������ť���򿪹����������õ�����
- ѡ��DB�����������ȷ��������á�

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Subnet-Business-Security-Access-Control/Step3-12.png)