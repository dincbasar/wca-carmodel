# (Undergraduate) Researcher Guide

We hope you find this document useful in your work, please feel free to email me at db1@cmu.edu for any clarifications or suggestions._

Welcome to Satyalab. This document is designed to facilitate your process of adapting to the environment, so you can start working on the important stuff as quickly as possible. We will first give quick definitions that are useful to know, then give the helpful bits about the timeline. 

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
* __Container__: A bounded virtual environment for an application to run in. They allow you to quickly export all the required dependencies of an application from a machine to another, along with other benefits. 
* __Docker__: A container service that will likely be used by you soon -- in the form "nvidia-docker". 
* __X-as-a-service__: Defines what is being given to the customer by the provider. X can be software, platform, infrastructure.

![alt-text](https://github.com/dincbasar/wca-carmodel/blob/master/Screen%20Shot%202019-04-22%20at%208.40.50%20PM.png)

_Taken from Microsoft Azure documentation._

* __Platform-as-a-service__: In Cloud systems, providing the necessary tools to develop, build, and run applications on remote machines. Basically, all the client needs to do is: build applications using the provided tools, and not worry about anything else. The more inclusive step is SaaS, where even the applications are provided to the customer. 
* __Neural Network__: A fundamental building block of many ML applications. It supports probabilistic learning, and can have multiple modes of output.
* __Convolutional Neural Network__: Unlike regular NN inputs, images have a significant amount of pixels. If all of these were used as parameters, the training would be extremely slow (if not impossible, depending on resolution). Therefore, image inputs to a CNN are _convoluted_, where a mask is applied to the input matrix to produce a (probably) smaller matrix that can be used to train the network on. This introduces multiple new hyperparameters, such as: the mask, stride (how many pixels to jump at each convolution), padding (what happens on edges of image matrix).
* __Recurrent CNN__: Read more [here](https://wiki.tum.de/display/lfdv/Recurrent+Neural+Networks+-+Combination+of+RNN+and+CNN) if needed. Might be a little unnecessary depending on your application.

### Satyalab Specific

* __WCA__: Stands for Wearable Cognitive Assistant, applications that run on wearable computers (smart glass, watch, ...).
* __Elijah__: Cloudlet based edge-computing, pushing the boundaries of both local resources and research at Satyalab :)
* __Gabriel__: Wearable Cognitive Assistant platform being built by the lab. It is designed to enable the development of cognitive assistant applications primarily for smart glasses. As of April 2019, it is designed to run on Android devices only.

![alt-text](https://github.com/dincbasar/wca-carmodel/blob/master/Screen%20Shot%202019-04-22%20at%2011.18.23%20PM.png)

* __TPOD__: Stands for A Tool For Painless Object Detection. It is used to train a [faster-RCNN](https://arxiv.org/pdf/1506.01497.pdf) instance to help with object detection in cognitive assistants. It features a basic tracking model to help with labeling frames. See the section below for further details.

___ 

## Expected Timeline

### Training the TPOD Application

1) Figure out a useful process to develop a WCA in. Some questions to consider:
  * Will people actually use it in the future? Does it serve as an example of what Gabriel can achieve?
  * How easy will it be to repeat the process in a lab environment? 
  * How much time do you have to build the application? If you only have weeks, go as basic as possible. 
  * Is the application possible using a smart glass with input and output capabilities on sound & video? A process where guidance can be distracting (like driving a car) might not be a good application.  
  
2) If you are able to use TPOD for your application (ask your supervisor about this): get started with taking training videos. Start basic with the number of distinct object classes you are trying to detect, then add more as you build experience. Always keep your use environment (where/how/when will the glass wearer use this application) in mind in this step to take the most applicable videos possible. Some features of useful videos:
  * Landscape (horizontal) videos only. Do not take vertical ones, as TPOD will not be happy with that.
  * Use false positives ( objects that are similar to the one you are trying to detect, but definitely not what the exact object) in the background, especially items that can be found in your use environment. These will help the RCNN not make mistakes.
  * Consider the lighting conditions of the use environment. If you are building for the outdoors, do not take your videos inside. If you are building for indoors, make sure to use multiple levels and types of lighting, as these can significantly change the accuracy of the RCNN. 
  * Video length is variable, but 8-10 seconds is usually enough to get enough frames (around 400-600) for a certain environment. 
  * Keep movement low (if this is not against your application), but do not completely eliminate it. Some movement will result slightly-out-of-focus frames that are harder but probably useful to detect. In the end, there will be significant head movement with the glass, so losing track with low motion is probably not a good feature for your application. If the training video includes quick movement, the basic tracker on TPOD will not be able to follow the frames. This will cause you to manually label many more frames than what is ideal.
  * Think of your use environment to determine what object view characteristics you want. Would you like to be able to detect objects that are partially obstructed? Partially out of frame? Held in hand? Merged with another object?
  * Any background restrictions you might use is a critical choice in design. Discuss this with your supervisor early, according to the needs of your application. A background restriction can be: requiring the user to have a white paper working space, so that you can limit the object detection space.
  * Take many videos, at least 10. There is a limit on how many frames should be used for each object, but that is presumably far away from what you can reach. 

3) Create the required labels for the distinct objects you want to detect, and start labeling the frames.
  * Just in case there is a system error, save your work frequently (there is no auto-save), otherwise your work since the last save will be entirely discared. 
  * If there are no labels in a frame, it is entirely discarded. This is useful if the object is blurry, obstructed, or if you just don't want to use certain parts of the training video.
  * __important__ If you are labeling a frame, either label it completely or include no labels at all. If a visible instance of the object is not labeled in a frame that has other objects labeled, your accuracy will drop. 
  * Use the tracker to your advantage: after labeling an object, wait for a second or two, then observe next frames as long as the labels are not accurate. For instance, the example below would be bad if we were training TPOD on tires (the black circular objects), because other objects are labeled in the frame, but tires are not. 
  * Label the entire object in frames. With motion, the tracker might switch to including only parts of the object. Correct these, and wait for the tracker again. 
  * It is fine to have label bounds overlap, since TPOD only does upright rectangles. For instance, the following is perfectly OK: 
<img src="https://github.com/dincbasar/wca-carmodel/blob/master/Screen%20Shot%202019-04-22%20at%209.55.39%20PM.png" width="250">
  
4) Submit the labeled videos for training. You are given the option to pick the videos and labels (distinct objects) that you would like to train your model on. Epoch = 10K or 20K is a good choice, and pick the faster-RCNN model for training. This process will take approximately an hour.

5) From here onwards, you will need access to a GPU machine. Talk to your supervisor to obtain access. __For CMU students:__ As of April 2019, one is available on cloudlet012.elijah.cs.cmu.edu. You can contact [Tom Eiszler](mailto:teiszler@cs.cmu.edu) to create an account.

### Testing (system-design dependent)

Now that you have a trained RCNN model, it is a good idea to test it and find all of its inaccuracies and mistakes. These will help you figure out how you can improve your training videos. 

1) SSH (or connect in some other form) into your GPU machine. 
* If you are not on the CMU campus network, you will need to use [VPN](https://www.cmu.edu/computing/services/endpoint/network-access/vpn/how-to/index.html). Pick the Library Resources VPN from the drop-down menu when you get to the login option. 
* You will need sudo access (most likely) to install packages, so make sure you have it. 

2) If you are the first to set up the machine, you will need to set up a firewall. The easiest way is to use `uwf`
```
# Update apt, package manager for linux: 
sudo apt-get update 

# uwf, a simple firewall program
sudo apt-get install uwf

# add the CMU ip addresses, or your own if needed (google "ip address" to get yours)
sudo uwf allow from 128.237.0.0/16 # [or replace IP address as required]
sudo ufw allow from 128.2.0.0/16  # [or replace IP address as required]

# deny all incoming and allow all outgoing by default
sudo uwf default deny incoming
sudo uwf default allow outgoing

# start the firewall, no other user will be able to access after this line runs
sudo ufw enable
```

3) Your machine might not have the necessary packages to run the RCNN clasifier. Apt is a useful package manager to do all of these quickly. Here is a general overview of what you might need to install:
```
# (Skip this line if you did step 2) Update apt, package manager for linux: 
sudo apt-get update 

# Install python3
sudo apt-get install python3 

# pip3, package manager for python3
curl https://bootstrap.pypa.io/get-pip.py --output get-pip.py 
python3 get-pip.py

# docker, the container service, not mandatory but still useful
sudo apt-get install docker

# nvidia drivers, required by nvidia-docker
sudo apt-get install nvidia-container-runtime

# nvidia-docker, container service for TPOD
sudo apt-get install nvidia-docker2 

# restart docker if you had already started it before
restart docker
```

4) Get the deployment link from TPOD. Go to `http://cloudlet001.elijah.cs.cmu.edu:10000/classifier/list` and click _Export Classifier Image_ for the trained classifier. The final link should be something of the form `registry.cmusatyalab.org/junjuew/container-registry:X`

5) Run the docker container 

` nvidia-docker run -it -p 0.0.0.0:8000:8000 --rm --name `__`[insert desired name here] [insert link from step #4 here]`__`/bin/bash run_server.sh `



## Authors

* __Dinc Basar__
* __Junjue Wang__

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
* Mahadev Satyanarayanan
* Tom Eiszler
