# SpringBoot-IBM-MQ-ElasticAPM

## Introduction
Welcome to the `SpringBoot-IBM-MQ-ElasticAPM` repository. This project demonstrates the integration of a Java Spring Boot application with IBM MQ, instrumented using the Elastic APM (Application Performance Monitoring) agent. The application's primary functionality is to send and receive messages to and from IBM MQ.

## Quick Start with Docker
To expedite the setup of this application, it's recommended to use a Docker instance of IBM MQ. Follow the instructions in the following IBM Developer tutorial to set up IBM MQ in a container: [Connecting an app to a queue manager in containers](https://developer.ibm.com/tutorials/mq-connect-app-queue-manager-containers/).

## Configuration
After setting up IBM MQ, you need to update the `application.properties` file in the `resources` directory. Here is an example configuration:

```properties
spring.profiles.active=development
ibm.mq.queueManager=QM1
ibm.mq.channel=DEV.ADMIN.SVRCONN
ibm.mq.connName=localhost(1414)
ibm.mq.queue=sunman
ibm.mq.user=admin
ibm.mq.password=passw0rd
```

## Elastic APM Agent Setup
Place the Elastic Java APM agent in the resources directory. Ensure you have the correct version of the APM agent jar file (e.g., elastic-apm-agent-1.43.0.jar).


## Running the Application
To run the application, use the following command, replacing <REPLACE-WITH-YOUR-ELASTIC-APM-TOKEN> and <REPLACE-WITH-YOUR-ELASTIC-APM-SERVER> with your specific Elastic APM server details:
```
java -javaagent:../src/main/resources/elastic-apm-agent-1.43.0.jar \
-Delastic.apm.service_name=ibm-mb-test-app \
-Delastic.apm.secret_token=<REPLACE-WITH-YOUR-ELASTIC-APM-TOKEN> \
-Delastic.apm.server_url=https://<REPLACE-WITH-YOUR-ELASTIC-APM-SERVER>.elastic-cloud.com:443 \
-Delastic.apm.environment=test \
-Delastic.apm.application_packages=org.example,javax.jms,java.net \
-jar demo-0.0.1-SNAPSHOT.jar

```



