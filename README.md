# Edge Platform Application Enablement Service

## Supported By [![N|Solid](https://www.nokia.com/sites/default/files/styles/original/public/media/nokia_logo_blue.png)](https://networks.nokia.com/)


* Main: [![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger) [![IntegrationTests](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/swagger-api/swagger-codegen)

The mobile edge platform, as defined in ETSI GS MEC 003 [[3]](https://www.etsi.org/deliver/etsi_gs/mec/001_099/003/01.01.01_60/gs_mec003v010101p.pdf), offers an environment where mobile edge applications may discover, advertise, consume and offer mobile edge services.

Via Mp1 reference point between the mobile edge platform and the mobile edge applications, as defined in ETSI GS MEC 003 [[3]](https://www.etsi.org/deliver/etsi_gs/mec/001_099/003/01.01.01_60/gs_mec003v010101p.pdf), some of the  basic functions are enabled such as **mobile edge service assistance, mobile edge application assistance, traffic routing, DNS rules, timing, transport information**.

[Details about mobile edge platform and application enablement API and other supporting functions](https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf)

[ETSI app enablement git lab](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api)


## Project Overview

* Implementation of Application Enablement service based on ETSI GS MEC 011 [[11]](https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf) standard

* [Supporting Functionalities](#FunctionalitiesSupport)

* **Implementation Supports**
   * Languages - [go](https://golang.org/)
   * ETSI MEC ISG MEC011 Compatible versions - [mec11v205](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api/raw/mec11v205-swagger2/Mp1.yaml)
   * Open API Specification 2.0 [mec11v205-swagger2 MP1.yaml](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api)

* [Contribution](#Contributing)

## Getting Started

If you want to build from source:

* [Prerequisites](#Prerequisites)

* You have a working [Go environment](https://golang.org/doc/install) and make sure [GO_PATH](https://github.com/golang/go/wiki/SettingGOPATH) is set properly.
```
      $ git clone  <githublink/edge-app-enablement-service>
      $ cd $GOPATH/src/edge-app-enablement-service
      $ make build
```
* [Run](#Run)

### Prerequisites

* [Java 7 or 8](http://java.oracle.com/)
* [Install maria DB](https://mariadb.com/kb/en/library/mariadb-package-repository-setup-and-usage/)

* **Create database and user**

  [root@localhost ~]$ mysql

  // create database namespace: appenabler\
  MariaDB [(none)]> CREATE DATABASE appenabler;

  // create database user: appenableruser\
  MariaDB [(none)]> CREATE USER 'appenableruser'@'%' IDENTIFIED BY 'R00t@r00t';

  // assign grant previleges to appenableruser\
  MariaDB [(none)]> grant all privileges on *.* to appenableruser@localhost identified by 'R00t@r00t' with grant option


### Run
#### export the env varibles

$ export DB_USER_NAME=appenableruser \
$ export DB_PASSWORD=UjAwdEByMDB0Cg== // base64 encoded R00t@r00t\
$ export DB_NAME=appenabler\
$ export DB_TYPE=mysql\
$ export DB_LISTENER_IP=127.0.0.1 // mysql service listner IP\
$ export DB_LISTENER_PORT=3306 // mysql service port

#### run test cases
$ cd $GOPATH/src/edge-app-enablement-service

$ make test

### running service
$ cd $GOPATH/src/edge-app-enablement-service

$ ./bin/AppEnabler

## Development

### Directory structure
```
$ cd $GOPATH/src/edge-app-enablement-service  
                                             - go (appenabler go module)
                                              - AppDB (AppDB go module)
```

**go directory** :  
            - appenabler go module\
            - http handlers and business logic
            
**AppDB directory** : \
            * database interaction with using go database sql driver\
            * DML, DDL queries

### Code Design flow
```
Flow: 
   [MEApplication POST/GET/PUT] -> [AppEnabler service]

Operations in App Enabler service:
   [http handler POST/GET/PUT] -> [Business Logic] -> [Database interaction]

```



### Tech
App enablement service uses a number of open source projects to work properly:

[openapi-generator](https://github.com/OpenAPITools/openapi-generator) - generating server stub code\
[sql](https://github.com/golang/go/tree/master/src/database/sql) - connecting to sql based database \
[MySQL Driver](https://github.com/go-sql-driver/mysql)



## FunctionalitiesSupport 
   * **mobile edge service assistance**
      * service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability
      * notify the changes of the mobile edge service availability to the relevant mobile edge application; ETSI 10 ETSI GS MEC 011 V1.1.1 (2017-07)
      * discovery of available mobile edge services

# for debugging
[root@localhost ~]# mysql
MariaDB [(none)]> use appenabler
MariaDB [appenabler]> show tables;
+-----------------------------------------+
| Tables_in_appenabler                    |
+-----------------------------------------+
| AppTerminationNotificationSubscription  |
| SerAvailabilityNotificationSubscription |
| SerAvailabilityNotification_v           |
| services                                |
+-----------------------------------------+

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Contributing

Want to contribute? Great!

If you would like to contribute, Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning
 
 need to update

## Authors

need to update

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
