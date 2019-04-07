# docker-example
Java boot, docker



To use dockerfile-maven-plugin you must add your docker server server to .m2/setting.xml under the servers tag:

<server>
  <id>docker.io</id>
  <username><user id></username>
  <password><password></password>
</server>

, and in your pom:
<useMavenSettingsForAuth>true</useMavenSettingsForAuth>

, I think the image you push must already exist on the server, so first time you must push manually with:
 docker push 