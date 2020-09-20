---


---

<h2 id="install-java">Install java</h2>
<pre><code>sudo apt-get update
sudo apt-get install openjdk-8-jdk
</code></pre>
<h2 id="install-maven">Install maven</h2>
<pre><code>sudo apt install maven
</code></pre>
<h2 id="install-tomcat7-recommand">Install tomcat7 (recommand)</h2>
<pre><code>cd /opt
wget http://www-us.apache.org/dist/tomcat/tomcat-7/v7.0.99/bin/apache-tomcat-7.0.99.tar.gz
</code></pre>
<h2 id="clone-java-server">Clone java server</h2>
<pre><code>git@git.digihcs.com:trunght/smh_gateway_zigbee.git
</code></pre>
<h2 id="install">Install</h2>
<pre><code>cd smh_gateway_zigbee
mvn clean install
</code></pre>
<h2 id="run-server">Run server</h2>
<pre><code>mvn tomcat7:run
</code></pre>

