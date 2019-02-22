# Edge Platform Application Enablement API Implementation

The mobile edge platform, as defined in ETSI GS MEC 003 [3], offers an environment where mobile edge applications may discover, advertise, consume and offer mobile edge services.

Via Mp1 reference point between the mobile edge platform and the mobile edge applications, as defined in ETSI GS MEC 003 [3], one of the  basic functions are enabled such as:

- mobile edge service assistance:
    - authentication and authorization of producing and consuming mobile edge serviceS
    - a means for service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability
    - a means to notify the changes of the mobile edge service availability to the relevant mobile edge
application
ETSI
10 ETSI GS MEC 011 V1.1.1 (2017-07)
    - discovery of available mobile edge services; 

For additional information about Application Enablement API and other supporting functions - https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf

For MP1.yaml gitlab -  https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api


## Project Overview
Part of this project we implemented mobile edge service assistance such as 
   - service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability
   - notify the changes of the mobile edge service availability to the relevant mobile edge
application; ETSI 10 ETSI GS MEC 011 V1.1.1 (2017-07)
- discovery of available mobile edge services


Implemented in go languge

## Getting Started

You have a working {Go environment}.

go get -d <githublink/edge-app-enablement-service>

cd $GOPATH/src/edge-app-enablement-service

make build



### Prerequisites


#### Install maria DB on VM/Baremetal

installation steps can find at https://mariadb.com/kb/en/library/mariadb-package-repository-setup-and-usage/

After installaing mariaDB Create User appenableruser:
[root@localhost ~]# mysql

// create namespace: appenabler

MariaDB [(none)]> CREATE DATABASE appenabler;

// create database user: appenabler

MariaDB [(none)]> CREATE USER 'appenableruser'@'%' IDENTIFIED BY 'R00t@r00t';

// assign grant previleges to appenableruser 

MariaDB [(none)]> GRANT ALL PRIVILEGES ON * . * TO 'appenableruser'@'%';

## Running the tests
### export the env varibles

export DB_USER_NAME=appenableruser
export DB_PASSWORD=UjAwdEByMDB0Cg== // base64 encoded R00t@r00t
export DB_NAME=appenabler
export DB_TYPE=mysql
export DB_MYSQL_LISTNER_IP=127.0.0.1 // mysql service listner IP
export DB_MYSQL_SERVICE_PORT=3306

### run test cases
make test 



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
