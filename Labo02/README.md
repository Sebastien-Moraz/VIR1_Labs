# Labo02 - Run a Spring App Locally

## Pedagogical intent
In this lab, we'll be taking the application we're going to evolve into our own hands, to discover the Spring architecture.

---

## Task 01 - Run the app

### Use Maven to package the solution

* [Maven Doc](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#build-the-project)

```bash
il faut en préalable ajouter le JAVA_HOME dans le fichier .zshrc

export JAVA_HOME=/usr/lib/jvm/jdk-17-oracle-x64
export PATH=$JAVA_HOME/bin:$PATH

relancer le terminal puis executer la commande suivante :

➜  ~ mvn package
```

* What operation does maven perform ?

```
Maven est un outil d'automatisation de build et de gestion de projet en Java. Il permet de compiler, de tester et de déployer des projets Java.
```

* What java dependencies are needed to make this work?

```
jdk-17-oracle-x64
```

* Where do we find the pre-compiled application after that?

```
In the Target folder
```

* Delete the folder containing the pre-compiled application, try again to observe the process.

* Is it a build ready for prod ?

```
No, it's a build for development
```

### Use Java to launch the application

* [The java command](https://docs.oracle.com/en/java/javase/14/docs/specs/man/java.html)

```bash
cd target
java -jar spring-petclinic-3.2.0-SNAPSHOT.jar
```

* Try to access to the app via your browser

```
it is accessible via the url : http://localhost:8080/
```

* You should get this page

![Home Page](img/webappSample.JPG)

* Stop the app

## Use the Spring Boot Maven plugin to launch the application

* [Maven plug in to run the app](https://docs.spring.io/spring-boot/docs/current/maven-plugin/reference/htmlsingle/#run)

```bash
mvnw spring-boot:run
```

---

## Task 02 - Explore the app

### Kind of app

* How can we access a home page via our browser?

```
http://localhost:8080/
```

* Go to http://localhost:8080/owners/find and add an owner

* Using the search function, can you find it?

* Relaunch the application and try again. How is data persistence ensured?

```
It is not persistent, if we make a modification and we restart the application, we lose the modifications
```

* How many logic layers are implemented on this application?

```
view, controller, service, repository
```

---
## Task 03 - Docker - First Analysis

* At this stage of the analysis, can you imagine a little better what kind of needs Docker could help us with?

```
Docker can automate the deployment of the application, by creating containers for each part of the application
```

* Try to list the tasks to be carried out to obtain two tiers, one hosting the application part locally and the second tier using Docker for the database engine.

```
a first docker will deal with the centralization of data using a database

and the second docker will take care of the application with a prior configuration for the same database which will allow several instances of the application without risking losing data
```
