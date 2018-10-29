# JavaService-on-K8s
This project contains a super Java service that can immediatly run on K8s / GKE. This can be used as a template for new microservices that should run on K8s.

## Used Libs, Frameworks, Tools
I've used the following stuff to get this example up an running. 

- Java as programming language
- VSCode as IDE
- Maven as build tool
- Spark java framework for providing REST services
- SLF4J for logging 
- Docker for the container image creation
- Kubernetes Command Line Tool -> kubectl 

In order to run it on your own you at least need maven, docker and kubectl.

## How to build and run

### Maven Build 
`mvn clean package`

### Docker Build
`docker build .`


## Troubleshooting

After the maven build you can test the package with

```java -jar target/packaged-service-jar-with-dependencies.jar```

After the docker build you can test the container image with 

```docker run -p 8080:8080 <created_image_id>```


