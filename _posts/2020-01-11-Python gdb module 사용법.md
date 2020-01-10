# Python gdb module 사용법



___simplecommand.py___



<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">import</span>&nbsp;gdb</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">class</span>&nbsp;SimpleCommand(gdb.Command):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#a71d5d">def</span>&nbsp;__init__(self):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">#&nbsp;This&nbsp;registers&nbsp;our&nbsp;class&nbsp;as&nbsp;"simple_command"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;super(SimpleCommand,&nbsp;self).__init__(<span style="color:#63a35c">"simple_command"</span>,&nbsp;gdb.COMMAND_DATA)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#a71d5d">def</span>&nbsp;invoke(self,&nbsp;arg,&nbsp;from_tty):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">#&nbsp;When&nbsp;we&nbsp;call&nbsp;"simple_command"&nbsp;from&nbsp;gdb,&nbsp;this&nbsp;is&nbsp;the&nbsp;method</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">#&nbsp;that&nbsp;will&nbsp;be&nbsp;called.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#066de2">print</span>(<span style="color:#63a35c">"Hello&nbsp;from&nbsp;simple_command!"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#&nbsp;This&nbsp;registers&nbsp;our&nbsp;class&nbsp;to&nbsp;the&nbsp;gdb&nbsp;runtime&nbsp;at&nbsp;"source"&nbsp;time.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">SimpleCommand()</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>



![simplecommand.png](https://github.com/aht7525/aht7525.github.io/blob/master/img/simplecommand.png?raw=true)



__gdb.execute__ : gdb 명령을 사용할수 있게함

ex) gdb.execute('b*(주소값)'), gdb.execute('set pagination off'), gdb.execute('r')

int(__gdb.parse_and_eval("$rip")__) : rip 값을 반환

xxd "파일이름" | grep 찾을내용

objdump -d 파일 | grep xxd값
