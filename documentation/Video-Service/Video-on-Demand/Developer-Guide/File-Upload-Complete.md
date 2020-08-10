<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-文件上传回调" class="anchor" aria-hidden="true" href="#文件上传回调"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>文件上传回调</h1>
<h2><a id="user-content-事件类型" class="anchor" aria-hidden="true" href="#事件类型"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>事件类型</h2>
<p>视频文件上传到媒资空间后，会触发 FileUploadComplete 事件。</p>
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
<td>videoId</td>
<td>String</td>
<td>视频ID</td>
</tr>
<tr>
<td>fileUrl</td>
<td>String</td>
<td>文件地址</td>
</tr>
<tr>
<td>size</td>
<td>Long</td>
<td>文件大小</td>
</tr>
</tbody>
</table>
<h2><a id="user-content-内容示例" class="anchor" aria-hidden="true" href="#内容示例"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>内容示例</h2>
<blockquote>
<p>说明：<br>
当前仅视频点播仅支持 HTTP 回调，故回调内容即为 HTTP POST Request Body</p>
</blockquote>
<div class="highlight highlight-source-json"><pre>{
    <span class="pl-s"><span class="pl-pds">"</span>eventTime<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>2020-07-28T09:58:27.707Z<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>eventType<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>FileUploadComplete<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>fileUrl<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>https://s3.cn-north-1.jcloudcs.com/vod-storage-272769/source/2020/20200728/422/317bd090-c4cb-4a3e-b2da-2881bf541295.mp4<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>size<span class="pl-pds">"</span></span>: <span class="pl-c1">5874985</span>,
    <span class="pl-s"><span class="pl-pds">"</span>videoId<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>38b0eca4-ac76-4de6-b5bc-467e4cd09cbd<span class="pl-pds">"</span></span>
}</pre></div>
</article>
  </div>
