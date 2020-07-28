<img src="docs/images/wawa.jpg" width="100" height="100"/>

[![Build Status](https://travis-ci.org/openmrs/openmrs-core.svg?branch=master)](https://google.com/) [![Coverage Status](https://coveralls.io/repos/github/openmrs/openmrs-core/badge.svg?branch=master)](https://google.com/) [![SonarQube Badge](https://api.codacy.com/project/badge/Grade/a51303ee46c34775a7c31c8d6016da6b)](https://google.com/)

# POC on Authenticate  Guest Users

## Table of Contents

1. [Introduction](#Introduction)
2. [Prerequisites](#Prerequisites)
3. [Dependencies](#Dependencies)
4. [Configuration](#Configuration-Build-And-Runtime-for-Local-LIE-IPDev-IPTest-IPProd)
5. [Build And Deployment](#Build-And-Deployment)
6. [Design Details](#Design-Details)
7. [Support](#Support)
8. [References](#References)
9. [FAQ's](#FAQ's)
10. [License](#license)

## Introduction

This POC demonstrates authenticating guest users  with a JSON Web Token (jwt)

## Design References
* [Component Design](https://www.toptal.com/java/rest-security-with-jwt-spring-security-and-java)

## Prerequisites
### <ins>Tools/Software</ins>

* [Java Build System](https://wawaappdev.atlassian.net/wiki/spaces/KM/pages/328830959/Java)
* [Approved IDE](https://wawaappdev.atlassian.net/wiki/spaces/KM/pages/329352164/IDE)
   
### <ins>Wawa Build Time Dependencies</ins>

| Project Name         | Version       |  Project URL  |   
|:---------------------|:--------------|:--------------------------------------------------------|      
|  Spring boot starter parent         |    2.1.9.RELEASE        |  [Spring Boot Starter Parent](https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-parent) |


### <ins>Infrastructure</ins>

|Software              | Version       | Comment(s)  |   
|:---------------------|:--------------|:--------------------------------------------------------|      
|  Database H2        |    1.2.x      |    H2 In-memory Database |
|  Message Bus XX      |   NA        |   Not Aapplicable |

## Environment Variables

|Environment Variable Name | Type (Env or Secret)  |  Scope (Build or Runtime)    | Responsible Party for value  | Purpose | Comment(s)  |   
|:-------------------------|:----------------------|:-----------------------------|:-----------------------------|:--------|:------------|      
|  SERVICE_BASE_URL    |    Env        |    Build & Runtime       |  Integration Platform    |           |  Scope of this variable changes at run time|
 |  BUILD_NUMBER           |    Env        |    Build & Runtime       |  Integration Platform    |           |  It is pr_pull_number |         |  BUILD_HASH               |    Env        |    Build & Runtime       |  Integration Platform    |           |  It is github hash    |  
  |  APP_VERSION           |    Env        |    Build & Runtime       |  Application Developer   |           |  The app_version comes from              the helm chart.|
 |   GITHUB_TOKEN          |    Env        |    Build             |  Integration Platform    |This variable allows downloading npm packages published to the GitHub NPM Registry.   |  To be renamed to GIT_PACKAGE_MANAGER_TOKEN   |
|ENABLE_BUILD_DETAILS|Env| Build & Runtime|Application Developer|Control visibility of build and version number in UI application expected value:- true : to show details false : to hide details        |  Yet to be created. It will come from helm chart.|

## Consumed Services
| Service             | Discovery Address       |   
|:--------------------|:------------------------|   
|  NA      | Not Applicable  |


*Discovery address is the name in the Istio service mesh that is used to access a downstream service*

## Events Produced And Events Consumed
| Event               |  Event Schema          |  Description           |
|:--------------------|------------------------|------------------------|
| NA               |Not Applicable  | NA  |

## Logging

 This section should have critical logging messages that can be used to understand the health of this component or aid in the debugging of the component

*[Logging Standard](https://dzone.com/articles/logging-with-log4j-in-java)*

## Health Checks
| Endpoint             | Path               |   Content     |
|:--------------------|:--------------------|---------------|   
|  NA     |  NA         |  NA        |

*Endpoints and the decoder for the current state of the service and any dependent components*

## Build And Deployment
### Compilation
```bash
cd myapp
mvn clean package
```

### Run As Application
```bash
java -jar ./myapp.jar
```

### Build Container
```bash
Not Applicable
```

### Run In Local Kubernetes
```bash
Not Applicable
```

## Testing Instructions 
### Unit test cases
There are multiple unit test cases written to cover the different components of the application. However there is a global application test suite file _**UnitTests.java**_     that combines all the test cases in a logical manner to create a complete suite. It can be run from command prompt using the following command -

```
mvn clean test
```

## Design Details
### Entity Relationship Diagram

![your-UML-diagram-name](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/spiegel-im-spiegel/plantuml-sample/master/class-diagram-01.puml)

### Entity State Machine Diagram

![your-UML-diagram-name](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/spiegel-im-spiegel/plantuml-sample/master/class-diagram-01.puml)

### Dependent Downstream Services
Currently there are no dependent downstream services 

## Support

   ### i . Deployment status
   
   It is a POC, hence there is no Deployment 
   
   
   ### ii. How to view Health statistics
  One of the way to view Health Statistics of your application is by adding Spring Boot Actuator module ,it helps you monitor and manage your Spring Boot application by           providing production-ready features like health check-up, auditing, metrics gathering,   HTTP tracing etc.
  Please check references for more information .[How to view Health statistics of a Microservice ](https://www.callicoder.com/spring-boot-actuator/)
  
  
   ### iii. How to view Logs
   You can view logs by creating a custom Log File using a FileHandler, so that all the logging information is written to the file.
## Supporting Team(s)
 
* Engineering Team3
   
## FAQ's

[FAQ's]("https://google.com/)
   
## References
| Name |Link | Comments   | 
|:-----|:----|:-----------|
|Spring Security|https://spring.io/projects/spring-security | |
|JWT Authentication| https://community.auth0.com/t/jwt-token-for-guest-anonymous-unauthenticated-users/15653 | |
|Implementing JWT Authentication on Spring Boot APIs|https://auth0.com/blog/implementing-jwt-authentication-on-spring-boot/ |  |
|Using Anonymous Sessions for Guest Checkout|https://docs.commercetools.com/tutorial-anonymous-session |  |
