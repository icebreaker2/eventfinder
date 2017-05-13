# Event Finder
The **Event Finder** searches for local events in Oldenburg and its surroundings. The **Event Finder** uses the [Google Maps APIs](https://developers.google.com/maps/) to display the events on a map with various additional information about the location.

In addition, the EventFinder uses a **EventCrawler** to crawl for events at other websites.

## Installation
### Prerequisites
Jetty 9.3 requires Java 8 (or greater) to run. Make sure you have it installed. To install jetty follow this step-by-step guide:
```bash
wget -c http://repo1.maven.org/maven2/org/eclipse/jetty/jetty-distribution/9.3.12.v20160915/jetty-distribution-9.3.12.v20160915.tar.gz
tar xzf jetty-distribution-9.3.12.v20160915.tar.gz
mv jetty-distribution-9.3.12.v20160915 jetty9
sudo mv jetty9 /opt
sudo chmod u=rwx,g=rxs,o= /opt/jetty9

cp /opt/jetty9/bin/jetty.sh /etc/init.d/jetty
vim /etc/default/jetty
```
Copy this to your into the vim window:
```bash
JAVA=/usr/bin/java # Path to Java
NO_START=0 # Start on boot
JETTY_HOST=0.0.0.0 # Listen to all hosts
JETTY_ARGS=jetty.port=8085
JETTY_USER=icebreaker # Run as this user [ADD HERE]
JETTY_HOME=/opt/jetty9
```

### EventFinder
```bash
git clone https://github.com/icebreaker2/eventfinder.git
cd eventfinder
mvn clean install
```
Use the `target/eventfinder-1.0.war` to deploy the website.

### Database and the Crawler
You need to setup a database for the event entries (otherwise you will not see any events on the map later on). After you have done it you can add your database in the [config.properties](src/main/resources/config.properties). The database is then used to store new events found by the crawler or to request them while using the **EventFinder**.

To start the crawler just run the `main` within `de.EventCrawler.CrawlerMain` or build a `jar` with the given `MANIFEST.MF` within `de/META-INF/MANIFEST.MF` to let the crawler crawl til the end of time.

### Deploy
If you want to refine this **EventFinder** or adapt it you should start with your IDE. For *IntelliJ* follow the steps below:
1. In the `Run/Debug Configurations` settings select `Jetty Server` and then `local`. 
2. Set the `Application Server` to `/opt/jetty9` and the deployment artifact to `target/eventfinder-1.0.war` at the `Deployment` tab.
3. Press the `run` button

If you want to deploy the **EventFinder** on your server here some basic steps to do so:
1. Copy the `target/eventfinder-1.0.war` into your `/opt/jetty9/webapps/` dir.
2. Start the server by either running `java -jar start.jar` within your jetty home `/opt/jetty9/` or start the service by typing `service jetty start`.

If no further settings are done by yourself you should see the website at `http://localhost:8080/eventfinder-1.0/`. 

*ENJOY!*

## Backend Structure
There is a UML 2.0 Class diagramm description of the Server Backend:
![](backend.png)




