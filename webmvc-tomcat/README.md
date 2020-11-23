Spring Boot project with Spring MVC, Tomcat and Jackson.

To build and run the native application packaged in a lightweight container with `default` mode:
```
mvn spring-boot:build-image
docker-compose up
```

And then go to [http://localhost:8080/](http://localhost:8080/).

To run in Cloud-Run
```
export GCP_PROJECT_ID=your_gcp_project_id
docker tag webmvc-tomcat:0.0.1-SNAPSHOT eu.gcr.io/$GCP_PROJECT_ID/webmvc-tomcat
docker push eu.gcr.io/$GCP_PROJECT_ID/webmvc-tomcat
gcloud run deploy webmvc-tomcat --image eu.gcr.io/$GCP_PROJECT_ID/webmvc-tomcat --platform managed --region europe-west1 --max-instances 1 --memory 256Mi --timeout 180
Allow unauthenticated invocations to [webmvc-tomcat] (y/N)?  Y
```