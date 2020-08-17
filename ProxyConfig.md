


# NPM configuration
 Use these commands:
```bash
npm config set proxy http://username:password@host:port
npm config set https-proxy http://username:password@host:port
```
Or you can edit directly your ~/.npmrc file:
```bash
proxy=http://username:password@host:port
https-proxy=http://username:password@host:port
https_proxy=http://username:password@host:port
```
# Yarn configuration
Use these commands:
```bash
yarn.js config set proxy http://username:password@host:port
yarn.js config set https-proxy http://username:password@host:port
```
# Git configuration
Use the below command
```bash
git config --global http.proxy http://username:password@host:port
git config --global https.proxy http://username:password@host:port
```
Or Edit directly your ~/.gitconfig file:
```bash
[http]
        proxy = http://username:password@host:port
[https]
        proxy = http://username:password@host:port
```
# Maven configuration
Edit the proxies session in your ~/.m2/settings.xml file:
```xml
<proxies>
    <proxy>
        <id>id</id>
        <active>true</active>
        <protocol>http</protocol>
        <username>username</username>
        <password>password</password>
        <host>host</host>
        <port>port</port>
        <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
    </proxy>
</proxies>
```
## Maven Wrapper
Create a new file .mvn/jvm.config inside the project folder and set the properties accordingly:
```bash
-Dhttp.proxyHost=host 
-Dhttp.proxyPort=port 
-Dhttps.proxyHost=host 
-Dhttps.proxyPort=port 
-Dhttp.proxyUser=username 
```
# Gradle configuration
Add the below in your gradle.properties file and in your gradle/wrapper/gradle-wrapper.properties file if you are downloading the wrapper over a proxy

If you want to set these properties globally then add it in USER_HOME/.gradle/gradle.properties file
```bash
## Proxy setup
systemProp.proxySet="true"
systemProp.http.keepAlive="true"
systemProp.http.proxyHost=host
systemProp.http.proxyPort=port
systemProp.http.proxyUser=username
systemProp.http.proxyPassword=password
systemProp.http.nonProxyHosts=local.net|some.host.com

systemProp.https.keepAlive="true"
systemProp.https.proxyHost=host
systemProp.https.proxyPort=port
systemProp.https.proxyUser=username
systemProp.https.proxyPassword=password
systemProp.https.nonProxyHosts=local.net|some.host.com
## end of proxy setup
-Dhttp.proxyPassword=password
```
