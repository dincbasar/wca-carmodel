# Undergraduate Researcher Guide

Welcome to Satyalab. This document is designed to facilitate your process of adapting and start working on the important stuff as quickly as possible. We will first give quick definitions to describe the environment, then give the helpful bits. 

## Wearable Cognitive Assistant Environment

Designed to go from basic to more complex, skip parts as needed.

### Basic

* __Distributed Network__: A system of computers that run specifics processes. For instance, your computer connecting with the Gmail server to send/receive emails. 
* __Latency__: The delay caused by data transfer from one computer to another. 
* __Bandwidth__: The amount of data that can be transferred from one computer to another in given time.
* __Local Computing__: Your computer running a program. Since there is no data transfer involved, there is no latency, but your computer might not be the best choice to run certain programs. 
* __Cloud Computing__: Your computer asking some other computer (usually rented, examples: Amazon AWS, Microsoft Azure) to run a program over the internet, and receiving the output. High network latency, but more powerful / purpose-specific computers possible. 
* __Cloudlet__: A computer that sits right inbetween your local machine and the cloud machines, to help with the network latency in operations that can be computed without the cloud machines. Example: Amazon Alexa, Google Home. 
* __Edge computing__: Using intermediaries (like cloudlets) in the distributed system. Can help by caching data, performing basic operations. For instance, Google Home device can listen to and analyze speech to detect "Hello Google" wake-up command. Sending 24h non-stop speech data to Google Servers would be very inefficient and use significant data. 
* __X-as-a-service__: Defines what is being given to the customer by the provider. X can be software, platform, infrastructure.

![alt-text](https://github.com/dincbasar/wca-carmodel/blob/master/Screen%20Shot%202019-04-22%20at%208.40.50%20PM.png)

_Taken from Microsoft Azure documentation._

* __Platform-as-a-service__: In Cloud systems, providing the necessary tools to develop, build, and run applications on the cloud. Basically, all the client needs to do is build applications using the tools, and not worry about anything else. 

### Satyalab Specific

* __Elijah__: Cloudlet based edge-computing, pushing the boundaries of both local and research at Satyalab :)
* __Gabriel__: Wearable Cognitive Assistant platform being built by the lab. It is designed to enable the development of cognitive assistant applications primarily for smart glasses. As of April 2019, it is designed to run on Android devices only.
* __TPOD__: Stands for A Tool For Painless Object Detection. It is used to train a [faster-RCNN](https://arxiv.org/pdf/1506.01497.pdf) instance to help with object detection in cognitive assistants. It features a basic tracking model to help with labeling frames. Further details later (Link Part Here).

___ 

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
