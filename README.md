# KrakenDS

Kraken Data Service, the REST connector for CICS, build on IIB10 and running on * [docker](https://github.com/ot4i/iib-docker).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Download and install IBM Integration Bus 10 Toolkit from * [here](http://www-01.ibm.com/support/docview.wss?uid=swg24042654).
For IIB10 on docker follow the instructions in *[ot4i project](https://github.com/ot4i/iib-docker).

### Installing

Installing Kraken DS requires four simple steps:

 * Create the Excecution Server (effective runtime of IBM Integration Bus).
 * Create the configurable service for the CICSRequest node.
 * Set the dbparams with the user and password of the Security Identity.
 * Deploy the file broker (BAR file) KrakenDS.bar.

Find the iib.sh command inside the docker, usualy:

```
cd /opt/ibm/iib-10.0.0.10
```

Create the Execution Server:

```
./iib mqsicreateexecutiongroup <Execution Node name (Broker)> -e <Excecution server name>
```
For example:

```
./iib mqsicreateexecutiongroup KRAKENNODE -e krakenexcec
```
Creating the configurable service:

```
./iib mqsicreateconfigurableservice KRAKENNODE -c CICSConnection -o ESB2CICS -n cicsServer, securityIdentity -v tcp://<IP o nombre del servidor CICS>,cicsSI
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

* Hat tip to anyone who's code was used
* Inspiration
* etc

