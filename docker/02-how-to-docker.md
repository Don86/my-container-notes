### Common Commands
* `docker images` - list images you've downloaded locally. 
* `docker run {appname:tag}` - instantiate container from image. Running this will *create a new container every time*, it doesn't re-use a previously created container. CTRL*-C to exit the process. You don't have to `pull` an image first; `docker run...` will `pull` the image automatically if it can't find it locally, which is a bit too magical. 
* `docker run -d {appname:tag}` - "d" is for "detached". Run container in background. 
* `docker ps` - list running containers, with respective container IDs. Note: docker automatically generates a random name for the container if you don't specify one. 
* `docker ps -a` - list all containers, running or not.
* `docker logs {container_id}` - print out logs associated with `{container_id}`. You can use `{container_name}` as well. 
* `docker stop {container_id}` - stop container. You can use `{container_name}` as well. 
### Run Container With Port Binding
After `docker run`, we can't actually use the container yet; we need to expose the container port to the `host` (the machine the container runs on, e.g. your laptop). This process is called *port binding*. 
* Every app has a standard port which it always runs on, e.g. NGINX always runs on port 80, redis on 6379.
* Port binding (looks and feels like port forwarding): when doing docker run, add more flags: `docker run -d -p {host_port}:{container_port} {app_name}:{tag}`. `-p` is for "publish". You can choose any `host_port` you want, usually 8000, or 8080, or something like that. e.g. `docker run -d -p 8080:80 nginx:1.13`. You can now visit your browser and visit `localhost:8080` to see the NGINX landing page. 
* If you run `docker ps`, you'll see port binding information listed as well. 
### Start And Stop Containers
As you may have guessed:
* `docker start {container_id}`
* `docker stop {container_id}`

### Private Registries & Repositories
* A place to keep your own docker images.
* All cloud vendors will have a service for your own docker images, e.g. AWS ECR. 
* Dockerhub offers private registries as well. 
* A *registry* is a collection of *repositories*, e.g. AWS ECR, Dockerhub are registries. A repo is a collection of related images with same name but different versions. 

### Dockerfiles

