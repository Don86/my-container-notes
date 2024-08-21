### Overview of Features
* Back in the day, when the internet was young, the web server was just an ordinary machine that sent out HTML files in response to client requests. That piece of software which handled requests was NGINX. 
* **NGINX as Load Balancer** - as the interwebs became more popular, we needed multiple machines/servers to handle increased traffic. We still needed NGINX to manage requests to/from the multiple servers. 
* **NGINX as Proxy Server** - "proxy" = to act on behalf of another agent. So "proxy server" = intermediate server that forwards client requests to other servers. NGINX is the first point of contact for incoming client requests, like a concierge, which then forwards the requests to backend servers, depending on some load balancing algo. 
* **Caching** - Cache responses from backend servers for frequently requested resources. 
* **Single Entrypoint (Security)** - Only the NGINX server is publicly accessible, greatly reducing the surface area of attack. Also easy to harden a single point of vulnerability. 
* **Moar Features**
	* **Compression** - e.g. NFLX uses nginx to compress video content before sending. 
	* **Segmentation** - sends the file in smaller chunks (video streaming). 
### Config
* the main config file is `nginx.conf`, usually located in `etc/nginx/`. 
* Uses a custom syntax comprising **directives** and **blocks**.
#### NGINX As K8s Ingress Controller
* That is: a proxy with load balancing functionality for K8s. 
* Handles routing incoming requests to appropriate service within the cluster, based on rules that we define in the ingress resource
* Note: the NGINX Ingress Controller acts as a load balancer *inside* the K8s cluster. **Not** publicly accessible. 
* A **Cloud load balancer** (e.g. AWS LB) handles incoming traffic from the internet, and forwards requests to the Ingress Controller. 