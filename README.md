# Edge Platform Application Enablement Service

**Supported by**<img src="https://www.nokia.com/sites/default/files/styles/original/public/media/nokia_logo_blue.png" ref="https://networks.nokia.com/" height="60">

* Master [![CircleCI](https://circleci.com/gh/helm/helm.svg?style=shield)](https://circleci.com/gh/helm/helm)
[![Go Report Card](https://goreportcard.com/badge/github.com/helm/helm)](https://goreportcard.com/report/github.com/helm/helm)
[![GoDoc](https://godoc.org/k8s.io/helm?status.svg)](https://godoc.org/k8s.io/helm)

The mobile edge platform, as defined in [ETSI GS MEC 003](https://www.etsi.org/deliver/etsi_gs/mec/001_099/003/01.01.01_60/gs_mec003v010101p.pdf), offers an environment where mobile edge applications may discover, advertise, consume and offer mobile edge services.

Via Mp1 reference point between the mobile edge platform and the mobile edge applications, as defined in ETSI GS MEC 003 [[3]](https://www.etsi.org/deliver/etsi_gs/mec/001_099/003/01.01.01_60/gs_mec003v010101p.pdf), some of the  basic functions are enabled such as **mobile edge service assistance, mobile edge application assistance, traffic routing, DNS rules, timing, transport information**.

[mobile edge platform and application enablement API and other supporting functions](https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf)

[ETSI app enablement git lab](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api)


## Project Overview

* Implementation of Application Enablement service based on ETSI GS MEC 011 [[11]](https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf) standard

* [Supporting Functionalities](#FunctionalitiesSupport)

* **Implementation Supports**
   * Languages - [go](https://golang.org/)
   * ETSI MEC ISG MEC011 Compatible versions - [mec11v205](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api/raw/mec11v205-swagger2/Mp1.yaml)
   * Open API Specification 2.0 [mec11v205-swagger2 MP1.yaml](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api)

* Contribution related information? [Contribution](#Contributing)

## Getting Started

If you want to build from source:

* [Prerequisites](#Prerequisites)

* [Buiding](#Building)
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

### Building

**Building binaries**
You have a working [Go environment](https://golang.org/doc/install) and make sure [GO_PATH](https://github.com/golang/go/wiki/SettingGOPATH) is set properly.
```
      $ cd $GOPATH/src
      $ mkdir -p github.com/edge-app-enablement-service
      $ cd github.com/edge-app-enablement-service
      $ git clone  <githublink/edge-app-enablement-service>
      $ cd $GOPATH/src/edge-app-enablement-service
      $ make build
```

**Building docker container**
 need to update

### Run
**export the env varibles**

$ export DB_USER_NAME=appenableruser \
$ export DB_PASSWORD=UjAwdEByMDB0Cg== // base64 encoded R00t@r00t\
$ export DB_NAME=appenabler\
$ export DB_TYPE=mysql\
$ export DB_LISTENER_IP=127.0.0.1 // mysql service listner IP\
$ export DB_LISTENER_PORT=3306 // mysql service port

**run test cases**
$ cd $GOPATH/src/edge-app-enablement-service

$ make test

**running service**
$ cd $GOPATH/src/edge-app-enablement-service

$ ./bin/AppEnabler

## Development

**Project structure**
```
$ cd $GOPATH/src/edge-app-enablement-service  
                                             - go
                                             - AppDB
```

**go modules**  
```
a) appenabler module:
      Location      -  go directory
      Functionality -  http handlers to receive messages  and business logic

b) AppDB module:
      Location      - AppDB directory
      Functionality - Database interaction with using go database sql driver
                    - DML, DDL queries
```

**Code Design flow**
```
Flow: 
   [MEApplication POST/GET/PUT] -> [AppEnabler service]

Operations in App Enabler service:
   [http handler POST/GET/PUT] -> [Business Logic] -> [Database interaction]

```

More information about the design flow etc.., please go refer Development.md file.


### Tech
App enablement service uses a number of open source projects to work properly:

[openapi-generator](https://github.com/OpenAPITools/openapi-generator) - generating server stub code\
[sql](https://github.com/golang/go/tree/master/src/database/sql) - connecting to sql based database \
[MySQL Driver](https://github.com/go-sql-driver/mysql)
(HTTP request multiplexer)https://github.com/gorilla/mux - Receving the Requests from MEApplications.


## FunctionalitiesSupport 
   * **mobile edge service assistance**
      * service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability
      * notify the changes of the mobile edge service availability to the relevant mobile edge application; ETSI 10 ETSI GS MEC 011 V1.1.1 (2017-07)
      * discovery of available mobile edge services

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
