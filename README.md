# Inject Openshift Secret and Reading it as an Environment Variables in Spring Boot

A simple "hello world" project for to display how we can inject sensitive variables into application's Environment Variables and read them.

## How to Run 
```
mvn spring-boot:run -DOPENSHIFT_APP_PASSWORD=whatever
```

## How to Test
```
curl -kv http://localhost:8080/
```

## Setting up Secret in Openshift
```
oc create secret generic mypassword --from-literal=OPENSHIFT_APP_PASSWORD=whatever
```

## Import App into Openshift
```
oc new-app registry.access.redhat.com/ubi8/openjdk-11~https://github.com/edwin/spring-boot-and-ocp-secret
``` 

## Inject Openshift Secret to Spring Boot App
```
oc set env --from=secret/mypassword dc/spring-boot-and-ocp-secret
``` 