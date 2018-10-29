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

### Image Taging and Pushing
In order to push the image to GCP you have to tag it with a fully qualified name
`docker tag <image-id> gcr.io/<gcp-project>/<give-it-name>`
Afterwards you can push it
`docker push gcr.io/<gcp-project>/<give-it-name>`

### Run it on K8N
`kubectl run <deployment_name> --image=gcr.io/<gcp-project>/<give-it-name>`
`kubectl expose <deployment_name> --port=8080 --target-port=80`

## Troubleshooting

### Authentication 
Use gcloud tools to help docker and kubectl with the right authentication
Therefore you have to correctly initialize the gcloud command line tool, login and set the right project id. 
Afterwards you can provision the authentication data into docker and kubectl

```gcloud auth configure-docker```
```gcloud container clusters get-credentials <cluster-name>```

### Check the Builds
After the maven build you can test the package with
```java -jar target/packaged-service-jar-with-dependencies.jar```

After the docker build you can test the container image with 
```docker run -p 8080:8080 <created_image_id>```



