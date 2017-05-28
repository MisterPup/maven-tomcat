=============================================
CONFIGURATION
=============================================

Aggiungere a tomcat-users.xml
<user username="tomcat" password="tomcat" roles="manager-gui,admin-gui,manager-script"/>

Per non schiantare username e password utilizza "server" come scritto qui
http://tomcat.apache.org/maven-plugin-2.2/tomcat7-maven-plugin/usage.html

~/.m2/settings.xml
<settings>
	<servers>
	<server>
	  <id>tomcat</id>
	  <username>tomcat</username>
	  <password>{A3p9n5EloPoHc+ElXPrxGbYjdTd6UEirLXFtzB35KMU=}</password>
	</server>
	</servers>
</settings>

pom.xml:
<configuration>
    <server>tomcat</server>
    <url>http://localhost:8080/manager/text</url>
    <path>/maven-tomcat</path>
</configuration>


=============================================
MAVEN
=============================================

Deploy
mvn tomcat7:deploy

Redeploy
mvn tomcat7:redeploy

Undeploy
mvn tomcat7:undeploy

Test
curl localhost:8080/maven-tomcat/demo/hello

=============================================
COMMAND LINE
=============================================

Deploy
curl --upload-file target/maven-tomcat.war "http://tomcat:tomcat@localhost:8080/manager/text/deploy?path=/maven-tomcat&update=true"

Undeploy
curl "http://tomcat:tomcat@localhost:8080/manager/text/undeploy?path=/maven-tomcat"