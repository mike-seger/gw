# gw
A spring cloud gateway application for development purposes.

To tart the gateway, simply run in the repository root (location of pom.xml):
````
mvn spring-boot:run


The example below makes the uri: http://localhost:18070/api1/ 

````
server:
    port: 18070
spring:
    cloud:
        gateway:
            routes:
            - id: route1
              uri: "https://www.google.com"
              predicates:
              - Path=/api1/**
              filters:
              - StripPrefix=1
              - AddRequestParameter=foo, bar
              - AddResponseHeader=X-SomeHeader, Bar
              
```` 

The test retriving the google home page:
````
curl http://localhost:18070/api1/
````
