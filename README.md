# Edge Platform Application Enablement API Implementation

## Supported By [![N|Solid](https://www.nokia.com/sites/default/files/styles/original/public/media/nokia_logo_blue.png)](https://networks.nokia.com/)


[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

The mobile edge platform, as defined in ETSI GS MEC 003 [3], offers an environment where mobile edge applications may discover, advertise, consume and offer mobile edge services.

Via Mp1 reference point between the mobile edge platform and the mobile edge applications, as defined in ETSI GS MEC 003 [3], one of the  basic functions are enabled such as **mobile edge service assistance, mobile edge application assistance, traffic routing, DNS rules, timing, transport information**.

[For additional information about Application Enablement API and other supporting functions](https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf)

[MP1.yaml](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api)


## Project Overview

* Implementation of Application Enablement service based on ETSI MEC MP1 standard

* **Functionalities Support**
   * **mobile edge service assistance**
      * service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability
      * notify the changes of the mobile edge service availability to the relevant mobile edge application; ETSI 10 ETSI GS MEC 011 V1.1.1 (2017-07)
      * discovery of available mobile edge services

* **Implementation Supports**
   * Languages - [go](https://golang.org/)
   * ETSI MEC ISG MEC011 Compatible versions - [mec11v205](https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api/raw/mec11v205-swagger2/Mp1.yaml)

## Getting Started

* [Prerequisites](#Prerequisites)

* You have a working [Go environment](https://golang.org/doc/install)
```
      $ git clone  <githublink/edge-app-enablement-service>
      cd $GOPATH/src/edge-app-enablement-service
      make build
```
* [Run](#Run)

### Prerequisites

* [Java 7 or 8](http://java.oracle.com/)
* [Install maria DB](https://mariadb.com/kb/en/library/mariadb-package-repository-setup-and-usage/)

* **Create database and user**

  [root@localhost ~]# mysql

  // create database namespace: appenabler\
  MariaDB [(none)]> CREATE DATABASE appenabler;

  // create database user: appenableruser\
  MariaDB [(none)]> CREATE USER 'appenableruser'@'%' IDENTIFIED BY 'R00t@r00t';

  // assign grant previleges to appenableruser\
  MariaDB [(none)]> grant all privileges on *.* to appenableruser@localhost identified by 'R00t@r00t' with grant option


## Run
### export the env varibles

export DB_USER_NAME=appenableruser \
export DB_PASSWORD=UjAwdEByMDB0Cg== // base64 encoded R00t@r00t\
export DB_NAME=appenabler\
export DB_TYPE=mysql\
export DB_LISTENER_IP=127.0.0.1 // mysql service listner IP\
export DB_LISTENER_PORT=3306 // mysql service port

### run test cases
cd $GOPATH/src/edge-app-enablement-service

make test

### running service
cd $GOPATH/src/edge-app-enablement-service

./bin/AppEnabler


### Tech
App enablement service uses a number of open source projects to work properly:

(openapi-generator)[https://github.com/OpenAPITools/openapi-generator] - generating server stub code\
(sql)[https://github.com/golang/go/tree/master/src/database/sql] - connecting to sql based database \
(MySQL Driver)[https://github.com/go-sql-driver/mysql]



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

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
