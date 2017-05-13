# Event Finder
The **Event Finder** searches for local events in Oldenburg and its surroundings. The **Event Finder** uses the [Google Maps APIs](https://developers.google.com/maps/) to display the events on a map and various different information about the location.

## Installation
### Prerequisites
Jetty 9.3 requires Java 8 (or greater) to run. Make sure you have it installed. To install jetty follow this step by step guide:
```bash
wget -c http://repo1.maven.org/maven2/org/eclipse/jetty/jetty-distribution/9.3.12.v20160915/jetty-distribution-9.3.12.v20160915.tar.gz
tar xzf jetty-distribution-9.3.12.v20160915.tar.gz
mv jetty-distribution-9.3.12.v20160915 jetty9
sudo mv jetty9 /opt
sudo chmod u=rwx,g=rxs,o= /opt/jetty9

cp /opt/jetty9/bin/jetty.sh /etc/init.d/jetty
vim /etc/default/jetty

JAVA=/usr/bin/java # Path to Java
NO_START=0 # Start on boot
JETTY_HOST=0.0.0.0 # Listen to all hosts
JETTY_ARGS=jetty.port=8085
JETTY_USER=icebreaker # Run as this user [ADD HERE]
JETTY_HOME=/opt/jetty9

service jetty start
```
The last command is actually not needed if you run the **EventFinder** within your IDE.

### EventFinder
```bash
git clone https://github.com/icebreaker2/eventfinder.git
cd eventfinder
mvn clean install
```
Use the `target/eventfinder-1.0.war` to deploy the website.

### Deploy
If you want to refine this **EventFinder** or adapt it you should start with your IDE. For *IntelliJ* follow the steps below:
1. 
2. 
3. 
4. 

If you want to deploy the **EventFinder** 

## Backend Structure
There is a UML Class diagramm description of the Server Backend:
![](backend.png)




