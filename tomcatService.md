```
[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking

#Environment=JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-armhf/jre
#Environment=CATALINA_PID=/opt/tomcat7/temp/tomcat.pid
#Environment=CATALINA_Home=/opt/tomcat7
#Environment=CATALINA_BASE=/opt/tomcat7
#Environment=’CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC’
#Environment=’JAVA_OPTS.awt.headless=true -Djava.security.egd=file:/dev/v/urandom’

ExecStart=/opt/tomcat7/bin/startup.sh
ExecStop=/opt/tomcat7/bin/shutdown.sh

User=root
UMask=0007
RestartSec=10
Restart=always

[Install]

WantedBy=multi-user.target

```
