# Graphene-SGX Secure Container (GSC)

GSC has been successfully merged into upstream Graphene. Please try GSC from Graphene repo instead: https://github.com/oscarlab/graphene/tree/master/Tools

## Introduction to GSC
Graphene-SGX Secure Container (GSC) is a container system where the containerized application can be protected by Intel:registered:SGX while it is running in a container environment. The GSC system includes two parts: (1) a Docker container instance where the application is running inside Graphene-SGX; (2) a front-end named GSCE (GSC Engine) which takes a legacy Docker container image and automatically launches the contained application inside a GSC container instance.

__** Disclaimer: This software is a research proof of concept and not intended for production use **_


## How to use GSC
Launching a GSC container instance includes following steps:

(1) Make sure there is a Docker container image of your application in the local or remote image repository.

(2) Prerequisites: 
    1. Intel SGX PSW/SDK https://github.com/intel/linux-sgx
    2. Intel SGX Driver https://github.com/intel/linux-sgx-driver

(2) Download and build Graphene-SGX, by executing:
    
    ./configure

(4) Launch a GSC container via the following command:

   bin/gsce run [All the arguments used for launching a normal Docker container] [Docker Image Name:Tag].
   
## Examples

Let's take redis, a key-value, in-memory database as an example. Assume the user runs a normal redis from its docker image as follows.

docker run -i -t -p 6379:6379 redis:latest

To launch a GSC container running redis, simply replace "docker" with "gsce", i.e., run the command as follows.

./gsce run -i -t -p 6379:6379 redis:latest


## Contact
For any questions, Please contact Li Lei with li.lei@intel.com
