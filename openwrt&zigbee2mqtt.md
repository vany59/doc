---


---

<h1 id="openwrt--zigbee2mqtt">OPENWRT &amp; ZIGBEE2MQTT</h1>
<p>Xem thêm về openwrt <a href="https://openwrt.org/">tại đây</a><br>
Xem thêm về zigbee2mqtt <a href="https://www.zigbee2mqtt.io/">tại đây</a></p>
<h3 id="download-and-install-openwrt">1. Download and install openwrt</h3>
<blockquote>
<p><strong><em>NOTE:</em></strong>  Openwrt hiện tại chưa có bản release chính thức cho raspberry pi 4, chỉ có bản snapshot (not recommended)</p>
</blockquote>
<p>link tải openwrt firmware cho rasberry pi <a href="https://openwrt.org/toh/raspberry_pi_foundation/raspberry_pi">tại đây</a></p>
<h4 id="windows">Windows</h4>
<ol>
<li><a href="https://sourceforge.net/projects/win32diskimager/">Download</a> app “win32 Disk Imager”</li>
<li>Cài đặt app</li>
<li>Mở app và flash openwrt firmware vào thẻ nhớ</li>
</ol>
<h3 id="ubuntu">Ubuntu</h3>
<ol>
<li><a href="https://www.balena.io/etcher/">Download</a> app “balenaEtcher”</li>
<li>Mở app và flash openwrt firmware vào thẻ nhớ</li>
</ol>
<blockquote>
<p><strong><em>NOTE:</em></strong> Openwrt chỉ sử dụng 1 phần nhỏ thẻ nhớ vì thế sau khi flash xong sẽ còn rất nhiều tài nguyên bị “unlocated” trong thẻ nhớ.</p>
</blockquote>
<h4 id="mở-rộng-tài-nguyên">Mở rộng tài nguyên</h4>
<h4 id="windows-1">Windows</h4>
<ol>
<li><a href="https://tuihocit.com/download-minitool-partition-wizard/">Download</a> tool “MiniTool Partition Wizard”</li>
</ol>
<h4 id="ubuntu-1">Ubuntu</h4>
<h3 id="clone-zigbee2mqtt">2. Clone zigbee2mqtt</h3>
<blockquote>
<p><strong><em>NOTE:</em></strong> Do openwrt không có sẵn git nên chúng ta cần clone zigbee2mqtt về trong thẻ nhớ</p>
</blockquote>
<pre><code>git clone https://github.com/Koenkk/zigbee2mqtt.git
</code></pre>
<p>Sau khi clone zigbee2mqtt gắn thẻ nhớ vào raspberry pi và bắt đầu khởi động.<br>
path zigbee2mqtt trong openwrt</p>
<pre><code>./
+--boot
	+--zigbee2mqtt
</code></pre>
<h3 id="cài-đặt-môi-trường-và-chạy-zigbee2mqtt">3. Cài đặt môi trường và chạy zigbee2mqtt</h3>
<ol>
<li>Update các opkg package</li>
</ol>
<pre><code>opkg update
</code></pre>
<ol start="2">
<li>Install kmod-usb-acm<br>
Để nhận zigbee doggle cần cài đặt package kmod-usb-acm</li>
</ol>
<pre><code>opkg install kmod-usb-acm
</code></pre>
<ol start="3">
<li>Install các package cần thiết</li>
</ol>
<ul>
<li>install node node-npm python-light python-dev make</li>
</ul>
<pre><code>opkg install node node-npm python-light python-dev make
</code></pre>
<ul>
<li>Install gcc</li>
</ul>
<blockquote>
<p><strong><em>NOTE:</em></strong> Cần phải install gcc riêng với các packages trên nếu không opkg không cài được gcc</p>
</blockquote>
<pre><code>opkg install gcc
</code></pre>
<ul>
<li>Install libpthread - thư viện bổ xung cho python</li>
</ul>
<pre><code>opkg install libpthread
ar -rc /usr/lib/libpthread.a
</code></pre>
<ul>
<li>Install prebuild-install</li>
</ul>
<pre><code>npm i -g prebuild-install
</code></pre>
<p>*Install dependencies cho zigbee2mqtt</p>
<pre><code>cd /boot/zigbee2mqtt
npm i
</code></pre>
<blockquote>
<p>Quá trình cài đặt mất tầm 5-10 phút</p>
</blockquote>
<h3 id="chạy-zigbee2mqtt">4. Chạy zigbee2mqtt</h3>
<p>Kết nối zigbee doggle vào rapberry pi</p>
<ul>
<li>Kiểm tra cổng của ziggbee doggle</li>
</ul>
<pre><code>ls /dev | grep ttyACM
</code></pre>
<p>Nếu khác <em>ttyACM</em> thì chúng ta thay đổi config trong zigbee2mqtt</p>
<pre><code></code></pre>
<ul>
<li>Chỉnh broker endpoint</li>
</ul>
<pre><code></code></pre>
<ul>
<li>Start zigbee2mqtt</li>
</ul>
<pre><code>npm start
</code></pre>

