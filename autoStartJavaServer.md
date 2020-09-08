---


---

<h1 id="create-auto-start-java-server">CREATE AUTO START JAVA SERVER</h1>
<h3 id="create-start-java-server-script">Create start java server script</h3>
<ol>
<li>add start server script<br>
add and edit file /script/server.sh</li>
</ol>
<pre class=" language-diff"><code class="prism  language-diff"><span class="token inserted">+ #!/bin/bash</span>

<span class="token inserted">+ cd /home/ubuntu/smh_gateway_zigbee &amp;&amp; mvn tomcat7:run &gt; /script/log &amp;</span>
<span class="token inserted">+  #whoami &gt; /script/log</span>
</code></pre>
<ol start="2">
<li>add service script<br>
add and edit file /etc/init.d/server</li>
</ol>
<pre class=" language-diff"><code class="prism  language-diff"><span class="token inserted">+ #!/bin/bash</span>
<span class="token inserted">+ ### BEGIN INIT INFO</span>
<span class="token inserted">+ # Provides:          haltusbpower</span>
<span class="token inserted">+ # Required-Start:    $all</span>
<span class="token inserted">+ # Required-Stop:</span>
<span class="token inserted">+ # Default-Start:     2 3 4 5</span>
<span class="token inserted">+ # Default-Stop:</span>
<span class="token inserted">+ # Short-Description: Halts USB power...</span>
<span class="token inserted">+ ### END INIT INFO</span>

<span class="token inserted">+ user=root</span>
<span class="token inserted">+ case "$1" in</span>
<span class="token inserted">+   start)</span>
<span class="token inserted">+     echo "Starting Service "</span>
<span class="token inserted">+     /script/server.sh</span>
<span class="token inserted">+     ;;</span>
<span class="token inserted">+   stop)</span>
<span class="token inserted">+     echo "Stopping Service "</span>
<span class="token inserted">+     ;;</span>
<span class="token inserted">+   *)</span>
<span class="token inserted">+     echo "Usage: /etc/init.d/server {start|stop}"</span>
<span class="token inserted">+     exit 1</span>
<span class="token inserted">+     ;;</span>
<span class="token inserted">+ esac</span>

<span class="token inserted">+ exit 0</span>
</code></pre>
<ol start="3">
<li>Enable server</li>
</ol>
<pre><code>sudo systemctl enable server
</code></pre>

