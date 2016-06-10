README
======

This document contains the info needed for running the MOAT functionality tests

##Installation
Clone this repository
```
git clone git@bitbucket.org:cosenmarcoaol/advisibilityautotest.git
cd advisibilityautotest
```

##Requirements
* [Java 7 JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* `java` and `jar` on the PATH
* [maven](https://maven.apache.org/)
* [Selenium Standalone Server](http://www.seleniumhq.org/download/)
* [Internet explorer Driver Server](http://www.seleniumhq.org/download/)
* [Google Chrome Driver](http://www.seleniumhq.org/download/) 


##Running the tests
Navigate to the directory where the selenium-server-standalone jar is placed, and run the following commands: 
```sh
cd path/to/selenium-server-standalone/

//Start the server
java -jar selenium-server-standalone-2.53.0.jar -role hub -hubConfig hub.json

//Start the node when running tests for Internet Exeplorer
java -Dwebdriver.ie.driver="PATH_TO_IE_DRIVER\IEDriverServer.exe" -jar selenium-server-standalone-2.53.0.jar -role node -nodeConfig node.json

OR

//Start the node when running tests for Google Chrome 
java -Dwebdriver.chrome.driver="PATH_TO_CHROME_DRIVER\chromedriver.exe" -jar selenium-server-standalone-2.53.0.jar -role node -nodeConfig node.json
```

Navigate to the automation tests directory ( path/to/advisibilityautotest ) and run the following commands:
```sh
cd path/to/advisibilityautotest

//1.Run the tests for Internet Explorer
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] -Dselenium.browser="internet explorer" verify

//2.Run the tests for Google Chrome
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] -Dselenium.browser=chrome verify

//3.Run the tests for Firefox
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] verify
```

##Running the tests with the production lib
```sh
//1.Run the tests for Internet Explorer
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df -Dproduction.library.url=http://aka-cdn-ns.adtechus.com -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] -Dselenium.browser="internet explorer" verify

//2.Run the tests for Google Chrome
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df  -Dproduction.library.url=http://aka-cdn-ns.adtechus.com -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] -Dselenium.browser=chrome verify

//3.Run the tests for Firefox
mvn -Dlibrary.version=adtechbrands092348fjlsmdhlwsl239fh3df  -Dproduction.library.url=http://aka-cdn-ns.adtechus.com -Dselenium.platform=WINDOWS -Dtest.host.alias=[HOST_ALIAS] verify
```