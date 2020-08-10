<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-视频转码回调" class="anchor" aria-hidden="true" href="#视频转码回调"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>视频转码回调</h1>
<h2><a id="user-content-事件类型" class="anchor" aria-hidden="true" href="#事件类型"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>事件类型</h2>
<p>视频某个转码任务完成时，会触发 StreamTranscodeComplete 事件。</p>
<h2><a id="user-content-回调内容" class="anchor" aria-hidden="true" href="#回调内容"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>回调内容</h2>
<table>
<thead>
<tr>
<th>字段名称</th>
<th>字段类型</th>
<th>字段描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>eventType</td>
<td>String</td>
<td>事件类型，特定值为 FileUploadComplete</td>
</tr>
<tr>
<td>eventTime</td>
<td>String</td>
<td>事件时间，为 UTC 时间的字符串表示，格式为 yyyy-MM-ddTHH:mm:ssZ</td>
</tr>
<tr>
<td>taskId</td>
<td>Long</td>
<td>任务ID</td>
</tr>
<tr>
<td>videoId</td>
<td>String</td>
<td>视频ID</td>
</tr>
<tr>
<td>title</td>
<td>String</td>
<td>视频标题</td>
</tr>
<tr>
<td>fileUrl</td>
<td>String</td>
<td>转码文件地址</td>
</tr>
<tr>
<td>format</td>
<td>String</td>
<td>转码文件格式</td>
</tr>
<tr>
<td>size</td>
<td>Long</td>
<td>转码文件大小，单位 Byte</td>
</tr>
<tr>
<td>duration</td>
<td>Float</td>
<td>转码视频时长，单位秒</td>
</tr>
<tr>
<td>fps</td>
<td>String</td>
<td>转码视频帧率</td>
</tr>
<tr>
<td>bitrate</td>
<td>String</td>
<td>转码视频码率</td>
</tr>
<tr>
<td>width</td>
<td>Integer</td>
<td>转码视频画面宽度，单位 px</td>
</tr>
<tr>
<td>height</td>
<td>Integer</td>
<td>转码视频画面高度，单位 px</td>
</tr>
<tr>
<td>definition</td>
<td>String</td>
<td>转码视频清晰度规格</td>
</tr>
<tr>
<td>shotImages</td>
<td>Array(String)</td>
<td>转码附带截图</td>
</tr>
<tr>
<td>status</td>
<td>String</td>
<td>转码任务状态</td>
</tr>
<tr>
<td>errorCode</td>
<td>String</td>
<td>错误码。视频转码出错的时候，会有该字段表示错误码</td>
</tr>
<tr>
<td>errorMessage</td>
<td>String</td>
<td>错误消息。视频转码出错的时候，会有该字段表示错误信息</td>
</tr>
</tbody>
</table>
<h2><a id="user-content-内容示例" class="anchor" aria-hidden="true" href="#内容示例"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>内容示例</h2>
<blockquote>
<p>说明：<br>
当前仅视频点播仅支持 HTTP 回调，故回调内容即为 HTTP POST Request Body</p>
</blockquote>
<div class="highlight highlight-source-json"><pre>{
  <span class="pl-s"><span class="pl-pds">"</span>bitrate<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>969177<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>definition<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>HD<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>duration<span class="pl-pds">"</span></span>: <span class="pl-c1">10.618</span>,
  <span class="pl-s"><span class="pl-pds">"</span>eventTime<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>2020-07-28T10:04:51.465Z<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>eventType<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>StreamTranscodeComplete<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>fileUrl<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/vod/product/28373149/959/1a541c2f55024fae92741e53d604e8f0.mp4<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>format<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>mp4<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>fps<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>25.000<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>height<span class="pl-pds">"</span></span>: <span class="pl-c1">1280</span>,
  <span class="pl-s"><span class="pl-pds">"</span>shotImages<span class="pl-pds">"</span></span>: [
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img1.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img2.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img3.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img4.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img5.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img6.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img7.jpg<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img8.jpg<span class="pl-pds">"</span></span>
  ],
  <span class="pl-s"><span class="pl-pds">"</span>size<span class="pl-pds">"</span></span>: <span class="pl-c1">1370362</span>,
  <span class="pl-s"><span class="pl-pds">"</span>status<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>success<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>taskId<span class="pl-pds">"</span></span>: <span class="pl-c1">959</span>,
  <span class="pl-s"><span class="pl-pds">"</span>title<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>1595930586758_filter-YiJianMeiHuamp4.mp4<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>videoId<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>e4b7e7d6-fe92-40b0-9870-fa10bb4d8ed5<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>width<span class="pl-pds">"</span></span>: <span class="pl-c1">596</span>
}</pre></div>
</article>
  </div>
