# Motivation - Why Use Containers?
These seem like dev env, not prod env, improvements. 
* Old scenario - every dev needs to install and config all services directly on their OS, on their VM. Postgres v15.1, Redis v7.0, etc. 
	* Installation process different for every OS
	* Multiple steps of installation where something can do wrong. Have you tried installing `R 4.x` and `tidyverse` on Ubuntu LFS lately?
* **With Containers** - `postgres` and all dependencies and configs would be packaged in 1 container. Instead of repeated `apt-gets` and seeing where installs failed due to dependencies, start the service as a Docker container using a Docker command, e.g. `docker run postgres` (which installs from Dockerhub). This Docker command is the same regardless of OS.  
* You can also run different versions of the same app without conflicts; they'll exist as distinct containers. 
### VMs vs. Docker Images
Front matter: OS's have 2 layers: OS Kernel (which interacts with hardware & software components, e.g. memory allocation, GPU) and OS Apps Layer (which runs software). 
* Docker virtualizes the OS Apps layer, VMs virtualize both OS layers
* Therefore, Docker images are often a few MB large, VM images are a few Gb. 
* Containers take milliseconds to start, VMs take minutes. 
* Docker images are OS-specific: e.g. compatible only with Linux distros, and have to check which flavours are supported. 
* Most containers for popular services are Linux based. `Docker Desktop` (for Win and Mac) allows you to run Linux-based containers. 

### Docker Images vs. Docker Containers
Container is to image as AWS EC2 VM is to AMI. 
* **Docker Image** - an executable application artifact, like a `.jar` file. However, unlike a `.jar` file, it not only contains application source code, but the complete environment configuration as well. 
* **Docker Container** - An actually running instance of an image. You can run multiple containers from 1 image. e.g. 

### Docker Registry
* These are repositories of ready-made Docker images, like how GH is a repository of open-source libraries. 
* `Dockerhub` is the most popular.
* Official images usually available, either by the companies themselves, or Docker community images that are officially verified
* Images are versioned as well (containing different versions of the same app). These are called *image tags*. The `latest` tag specifies the latest release. Selecting a specific version of an image is best practice in most cases. 
* Download the Docker image of your choice with `docker pull {name}:{tag}`, e.g. `docker pull nginx:1.13`. If `tag` isn't specified, the latest release is pulled. 

