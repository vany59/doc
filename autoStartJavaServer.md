---


---

<h1 id="create-auto-start-java-server">CREATE AUTO START JAVA SERVER</h1>
<h3 id="create-start-java-server-script">Create start java server script</h3>
<ol>
<li>add start server script<br>
add and edit file /script/server.sh</li>
</ol>
<pre><code>#!/bin/bash

cd /home/ubuntu/smh_gateway_zigbee &amp;&amp; mvn tomcat7:run &gt; /script/log &amp;
#whoami &gt; /script/log
</code></pre>
<ol start="2">
<li>add service script<br>
add and edit file /etc/init.d/server</li>
</ol>
<pre><code>#!/bin/bash
### BEGIN INIT INFO
# Provides:          haltusbpower
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Halts USB power...
### END INIT INFO

user=root
case "$1" in
  start)
    echo "Starting Service "
    /script/server.sh
    ;;
  stop)
    echo "Stopping Service "
    ;;
  *)
    echo "Usage: /etc/init.d/server {start|stop}"
    exit 1
    ;;
esac

exit 0
</code></pre>
<ol start="3">
<li>Enable server</li>
</ol>
<pre><code>sudo systemctl enable server
</code></pre>

