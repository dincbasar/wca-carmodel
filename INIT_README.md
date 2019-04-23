# Undergraduate Researcher Guide

Welcome to Satyalab. This document is designed to facilitate your process of adapting and start working on the important stuff as quickly as possible. We will first give quick definitions to describe the environment, then give the helpful bits. 

## Definitions

Designed to go from basic to more complex, skip parts as needed.

### General

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

* __Platform-as-a-service__: In Cloud systems, providing the necessary tools to develop, build, and run applications on remote machines. Basically, all the client needs to do is: build applications using the provided tools, and not worry about anything else. The more inclusive step is SaaS, where even the applications are provided to the customer. 
* __Neural Network__: A fundamental building block of many ML applications. It supports probabilistic learning, and can have multiple modes of output. __More pending Matt Gormley confirmation.__ 
* __Convolutional Neural Network__: Unlike regular NN inputs, images have a significant amount of pixels. If all of these were used as parameters, the training would be extremely slow (if not impossible, depending on resolution). Therefore, image inputs to a CNN are _convoluted_, where a mask is applied to the input matrix to produce a (probably) smaller matrix that can be used to train the network on. This introduces multiple new hyperparameters, such as: the mask, stride (how many pixels to jump at each convolution), padding (what happens on edges of image matrix). __More pending Matt Gormley confirmation.__ 
* __Recurrent CNN__: Read more [here](https://wiki.tum.de/display/lfdv/Recurrent+Neural+Networks+-+Combination+of+RNN+and+CNN) if needed. Might be a little unnecessary depending on your application.

### Satyalab Specific

* __WCA__: Stands for Wearable Cognitive Assistant, applications that run on wearable computers (smart glass, watch, ...).
* __Elijah__: Cloudlet based edge-computing, pushing the boundaries of both local resources and research at Satyalab :)
* __Gabriel__: Wearable Cognitive Assistant platform being built by the lab. It is designed to enable the development of cognitive assistant applications primarily for smart glasses. As of April 2019, it is designed to run on Android devices only.
* __TPOD__: Stands for A Tool For Painless Object Detection. It is used to train a [faster-RCNN](https://arxiv.org/pdf/1506.01497.pdf) instance to help with object detection in cognitive assistants. It features a basic tracking model to help with labeling frames. Further details [here](Link Part Here).

___ 

## Expected Timeline

1) Figure out a useful process to develop a WCA in. Some questions to consider:
  * Will people actually use it in the future? Does it serve as an example of what Gabriel can achieve?
  * How easy will it be to repeat the process in a lab environment? 
  * How much time do you have to build the application? If you only have weeks, go as basic as possible. 
  * Is the application possible using a smart glass with input and output capabilities on sound & video? A process where guidance can be distracting (like driving a car) might not be a good application.  
  * 
2) If you are able to use TPOD for your application (ask your supervisor about this): get started with taking training videos. Start basic with the number of distinct object classes you are trying to detect, then add more as you build experience. Always keep your use environment (where/how/when will the glass wearer use this application) in mind in this step to take the most applicable videos possible. Some features of useful videos:
  * Consider the lighting conditions of the use environment. If you are building for the outdoors, do not take your videos inside. If you are building for indoors, make sure to use multiple levels and types of lighting, as these can significantly change the accuracy of the RCNN. 
  * Use false positives ( objects that are similar to the one you are trying to detect, but definitely not what the exact object) in the background, especially items that can be found in your use environment. These will help the RCNN not make mistakes.
  * Length is variable, but 8-10 seconds is usually enough to get enough frames for a certain environment. 
  * Keep movement low (if this is not against your application), but do not completely eliminate it. Some movement will result slightly-out-of-focus frames that are harder but probably useful to detect. In the end, there will be significant head movement with the glass, so losing track with low motion is probably not a good feature. If the training video includes quick movement, the basic tracker on TPOD will not be able to follow the frames. This will cause you to manually label many more frames than what is ideal.
  * Think of your use environment to determine what object view characteristics you want. Would you like to be able to detect objects that are partially obstructed? Partially out of frame? 

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
