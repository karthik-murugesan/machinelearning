# Using various framework/tools over corporate proxy
If you are behind a corporate proxy,  use the following configuration to access different tools/frameworks over Corporate Proxy.

If you are behind the windows proxy, you can run cntlm to change the  NTLM authentication to normal HTTP Proxy. 

Supposing your proxy is defined with:

* username
* password
* host
* port
The resulting configuration is: http://username:password@host:port

If you use Cntlm, then your configuration would be: 127.0.0.1:3128. Otherwise, follow the next steps to configure each tool individually.

## Proxy Configuration

### Wget/Curl/pip
Use the below commands
```bash
export HTTP_PROXY=http://username:password@host:port
or
export HTTP_PROXY=http://domain\\username:password@host:port

export HTTPS_PROXY=$HTTP_PROXY
export http_proxy=$HTTP_PROXY
export https_proxy=$http_proxy
export ftp_proxy=$HTTP_PROXY
```
### Conda
```bash
export HTTP_PROXY=http://username:password@host:port
or
export HTTP_PROXY=http://domain\username:password@host:port

export HTTPS_PROXY=$HTTP_PROXY
export http_proxy=$HTTP_PROXY
export https_proxy=$HTTP_PROXY
```
### NPM configuration
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
### Yarn configuration
Use these commands:
```bash
yarn.js config set proxy http://username:password@host:port
yarn.js config set https-proxy http://username:password@host:port
```
### Git configuration
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
### Maven configuration
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
#### Maven Wrapper
Create a new file .mvn/jvm.config inside the project folder and set the properties accordingly:
```bash
-Dhttp.proxyHost=host 
-Dhttp.proxyPort=port 
-Dhttps.proxyHost=host 
-Dhttps.proxyPort=port 
-Dhttp.proxyUser=username 
```
### Gradle configuration
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
### Docker
#### Native Docker
Depending on your OS, you have to edit a specific file (/etc/sysconfig/docker or /etc/default/docker).

Then, you have to restart the docker service with: sudo service docker restart.

It will not apply to systemd. See this page from docker to configure the proxy.

#### Docker with docker-machine
You can create your docker-machine with:
```bash
docker-machine create -d virtualbox \
    --engine-env HTTP_PROXY=http://username:password@host:port \
    --engine-env HTTPS_PROXY=http://username:password@host:port \
    default
 ```
Or you can edit the file ~/.docker/machine/machines/default/config.json.
## Disable SSL Check for different tools
### wget
```bash
wget --no-check-certificate <url>
```
### Curl
```bash
curl -kFlo <url>
```
### Python
```bash
export PYTHONHTTPSVERIFY=0
```
### NPM
npm set strict-ssl false
