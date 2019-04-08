# docker-example




To use dockerfile-maven-plugin you must add your docker server server to .m2/setting.xml under the servers tag:

```
<server>
  <id>docker.io</id>
  <username><user id></username>
  <password><password></password>
</server>
```
, and in your pom add these properties:

```
<properties>
    <docker.image.prefix>oajamfibia</docker.image.prefix>
    <project.build.finalName>${project.artifactId}-${project.version}</project.build.finalName>
    <dockerfile-maven-version>1.4.10</dockerfile-maven-version>
</properties>
```
and the **spring-docker plugin** and

**maven-dependency-plugin**: to unpack the jar and the 
 
**dockerfile-maven-plugin**: to build the docker image 
 
**useMavenSettingsForAuth**-tag will use the server credentials in .m2/setting.xml 

Also add the Dockerfile.



I think the image you push must already exist on the server, so first time you must push manually with:
 ```docker push```
 
docker build and upload is now part of maven lifecycle
mvn deploy
, will: 
- build the jar
- unpack the jar (to add the dependencies separately to the docker image)
- build the docker image
- upload the docker image to the docker repository server, in this case docker.io


To run the image named oajamfibia/docker-example:0.1.1 in a local docker container, naming the container docker-example-container and open port 8080
```
docker run --name docker-example-container -p 8080:8080 -d oajamfibia/docker-example:0.1.1
```