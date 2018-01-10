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
./iib mqsicreateconfigurableservice KRAKENNODE -c CICSConnection -o KRAKENDS -n cicsServer, securityIdentity -v tcp://<IP o nombre del servidor CICS>,KRAKENSI
```
Creating the  Security Identity:

```
./iib mqsisetdbparms KRAKENNODE -n cics::KRAKENSI -u <usuario CICS> -p <clave del usuario CICS>
```
Restart the execution node for the changes to take effect:

```
./iib mqsistop KRAKENNODE 
./iib mqsistart KRAKENNODE
```

Deploy the Broker Archiver File (BAR File):

```
./iib mqsideploy KRAKENNODE -e krakenexcec -a </BARs Files URI>/KrakenDS.bar
```

## Contributing

Please read [CONTRIBUTING.md](https://github.com/israelcruzperez/krakends/blob/master/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/israelcruzperez/krakends/tags). 

## Authors

* **Israel Cruz** - *Initial work* - [linkedin](https://linkedin.com/in/israel-cruz-b9997429)

See also the list of [contributors](https://github.com/israelcruzperez/krakends/graphs/contributors) who participated in this project.



