# Edge Application Enablement Service Registry API Implementation

The mobile edge platform, as defined in ETSI GS MEC 003 [3], offers an environment where mobile edge applications
may discover, advertise, consume and offer mobile edge services. Upon receipt of update, activation or deactivation of
traffic rules from the mobile edge platform manager, applications or services, the mobile edge platform instructs the
data plane accordingly. The mobile edge platform also receives DNS records from the mobile edge platform manager
and uses them to configure a DNS proxy/server.

Via Mp1 reference point between the mobile edge platform and the mobile edge applications, as defined in ETSI
GS MEC 003 [3], the basic functions are enabled, such as: 

- authentication and authorization of producing and consuming mobile edge services;
- a means for service producing mobile edge applications to register towards the mobile edge platform the
mobile edge services they provide, and to update the mobile edge platform about changes of the mobile
edge service availability;
- a means to notify the changes of the mobile edge service availability to the relevant mobile edge
application; 
ETSI
10 ETSI GS MEC 011 V1.1.1 (2017-07)
- discovery of available mobile edge services; 

For additional information about Application Enablement API https://www.etsi.org/deliver/etsi_gs/MEC/001_099/011/01.01.01_60/gs_mec011v010101p.pdf

For additonal information about MEC Application Enablement API: https://forge.etsi.org/gitlab/mec/gs011-app-enablement-api


## Project Overview



## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
Give examples
```

### Installing

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

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
