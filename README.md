# Machine Learning Engineer Nanodegree
# Deep Learning
## Project: Build a Digit Recognition Program

### Install

This project requires **Python 2.7** and the following Python libraries installed:

- [NumPy](http://www.numpy.org/)
- [SciPy](https://www.scipy.org/)
- [scikit-learn](http://scikit-learn.org/0.17/install.html) (v0.17)
- [TensorFlow](http://tensorflow.org)

You will also need to have software installed to run and execute a [Jupyter Notebook](http://ipython.org/notebook.html).

In addition to the above, for those optionally seeking to use image processing software, you may need one of the following:
- [PyGame](http://pygame.org/)
   - Helpful links for installing PyGame:
   - [Getting Started](https://www.pygame.org/wiki/GettingStarted)
   - [PyGame Information](http://www.pygame.org/wiki/info)
   - [Google Group](https://groups.google.com/forum/#!forum/pygame-mirror-on-google-groups)
   - [PyGame subreddit](https://www.reddit.com/r/pygame/)
- [OpenCV](http://opencv.org/)

For those optionally seeking to deploy an Android application:
- Android SDK & NDK (see this [README](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/examples/android/README.md))

If you do not have Python installed yet, it is highly recommended that you install the [Anaconda](http://continuum.io/downloads) distribution of Python, which already has the above packages and more included. Make sure that you select the Python 2.7 installer and not the Python 3.x installer. `pygame` and `OpenCV` can then be installed using one of the following commands:

Mac:  
```bash
conda install -c https://conda.anaconda.org/quasiben pygame
conda install -c menpo opencv=2.4.11
```

Windows & Linux:  
```bash
conda install -c https://conda.anaconda.org/tlatorre pygame
conda install -c menpo opencv=2.4.11
```

### Code

A template notebook is provided as `digit_recognition.ipynb`. While no code is included in the notebook, you will be required to use the notebook to implement the basic functionality of your project and answer questions about your implementation and results. 

### Run

In a terminal or command window, navigate to the top-level project directory `digit_recognition/` (that contains this README) and run one of the following commands:

```bash
ipython notebook digit_recognition.ipynb
```  
or
```bash
jupyter notebook digit_recognition.ipynb
```

This will open the Jupyter Notebook software and notebook file in your browser.


### Data

While no data is directly provided with the project, you will be required to download and use the [Street View House Numbers (SVHN) dataset](http://ufldl.stanford.edu/housenumbers/), along with either the [notMNIST](http://yaroslavvb.blogspot.com/2011/09/notmnist-dataset.html) or [MNIST](http://yann.lecun.com/exdb/mnist/) datasets. If you've completed the course material, the **notMINIST** dataset should already be available.

Examples from Getting Started with Tensorflow by Giancarlo Zaccone
===========================================================


Building and Running the Docker container 
===========================================

Building a local Docker image
---------------------------------

    cd Getting_Started_Tensorflow
    docker build --pull -t $USER/assignments .

Check that image was created
---------------------------------
	docker images

Running the local container from the image
---------------------------

To run a disposable container (Work not saved!):

    docker run -p 8888:8888 -it --rm $USER/assignments

Note the above command will create an ephemeral container and all data stored in the container will be lost when the container stops.

To avoid losing work between sessions in the container, it is recommended that you mount the `tensorflow/examples/udacity` directory into the container:

    docker run -p 8888:8888 -v </path/to/Getting_Started_TensorFlow>:/notebooks -it --rm $USER/assignments

This will allow you to save work and have access to generated files on the host filesystem.

On Windows, mount directories using:

	docker run -p 8888:8888 -v //c/path/to/Getting_Started_TensorFlow>:/notebooks -it --rm $USER/assignments

Accessing the Notebooks
-----------------------

On linux, go to: http://127.0.0.1:8888

On mac, find the virtual machine's IP using:

    docker-machine ip default

Then go to: http://IP:8888 (likely http://192.168.99.100:8888)

FAQ
---

* **I'm getting a MemoryError when loading data in the first notebook.**

If you're using a Mac, Docker works by running a VM locally (which
is controlled by `docker-machine`). It's quite likely that you'll
need to bump up the amount of RAM allocated to the VM beyond the
default (which is 1G).
[This Stack Overflow question](http://stackoverflow.com/questions/32834082/how-to-increase-docker-machine-memory-mac)
has two good suggestions; we recommend using 8G.

In addition, you may need to pass `--memory=8g` as an extra argument to
`docker run`.

* **I want to create a new virtual machine instead of the default one.**

`docker-machine` is a tool to provision and manage docker hosts, it supports multiple platform (ex. aws, gce, azure, virtualbox, ...). To create a new virtual machine locally with built-in docker engine, you can use

    docker-machine create -d virtualbox --virtualbox-memory 8196 tensorflow
    
`-d` means the driver for the cloud platform, supported drivers listed [here](https://docs.docker.com/machine/drivers/). Here we use virtualbox to create a new virtual machine locally. `tensorflow` means the name of the virtual machine, feel free to use whatever you like. You can use

    docker-machine ip tensorflow
    
to get the ip of the new virtual machine. To switch from default virtual machine to a new one (here we use tensorflow), type

    eval $(docker-machine env tensorflow)
    
Note that `docker-machine env tensorflow` outputs some environment variables such like `DOCKER_HOST`. Then your docker client is now connected to the docker host in virtual machine `tensorflow`

* **I'm getting a TLS connection error.**

If you get an error about the TLS connection of your docker, run the command below to confirm the problem.

	docker-machine ip tensorflow

Then if it is the case use the instructions on [this page](https://docs.docker.com/toolbox/faqs/troubleshoot/) to solve the issue.


* **I'm getting the error - docker: Cannot connect to the Docker daemon. Is the docker daemon running on this host? - when I run 'docker run'.**

This is a permissions issue, and a popular answer is provided for Linux and Max OSX [here](http://stackoverflow.com/questions/21871479/docker-cant-connect-to-docker-daemon) on StackOverflow.

