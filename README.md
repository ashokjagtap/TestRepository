# Persomap - Unique User Manager (UUM) project.

## NOTE
Persomap module is basically mapping the user ids and following 3 different API are implemented for Same.
* SetUserMapping(AdsWizzUserID,PartnerUserID,Domain, IDType)
* GetPartnerUserId(AdsWizzUserId,Domain,IDType) 
* GetAdsWizzUserId(PartnerUserID,Domain,IDType) 

## Development
### Prepare your environment
Following are pre-requisites to prepare environment.

* Make sure that Java1.7 and Maven should be installed on machine.
* Download source code from GitHUB<<https://github.com/adswizz/cybage-persomap>>
* Modify the environment specific parameters from file 'src/main/resource/persomap-config.yml'

##### AWS Configuration
* access_key_id : AWS_ACCESS_KEY_ID
* secret_access_key : AWS_ACCESS_SECRET_KEY

##### DynamoDB Configuration
* dynamodb_table_name : DYNAMODB_TABLE_NAME
* aws_endpoint_url : http://IpAddress:port

##### Elastic Cache Configuration
* aws_cache_url : IPAddress:port

##### Server port Configuration
server:
applicationConnectors:
- type: http
port: 80
adminConnectors:
- type: http
port: 8081

* Environment_name : DEV - This value should take care the creation of dynamodb-local instance and For prodcution value should be 'PROD'.

## Build
** Build from the command line **

* To Create the new persomap jar use following command.
```javascript
  mvn clean install
```

Check that a new jar will be created under /target folder.

* If you don't want to run the test cases then skip test cases by using command -
```javascript
  mvn clean install -Dmaven.test.skip=true
```

* Goto /target folder and open command prompt and run the application using command as 
```javascript
 'java -jar <<Generated_JAR_NAME>> server persomap-config.yml'
  e.g -  java -jar persomap.jar server persomap-config.yml
``` 
 
* Check the application health on admin port using url as 'http://localhost:8081'

* Check the Swagger API on application port using url as http://localhost:80/swagger

## pre-requisites for local Development(Windows)

* Download the memcached client from site http://memcached.org/downloads and run memcached.exe file.

* For local DynamoDB instance download it from http://dynamodb-local.s3-website-us-west-2.amazonaws.com/dynamodb_local_latest.zip and unzip it and open  command prompt in same folder and run it with command
```javascript
 'java -Djava.library.path=./DynamoDBLocal_lib -jar DynamoDBLocal.jar'
```

* environment_name : DEV
 Keep environment name as DEV for locally only, This will automatically create a local DynamoDB table.

## Release Notes
