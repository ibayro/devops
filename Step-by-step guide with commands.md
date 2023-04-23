### Step-by-step guide with commands and detailed explanation

In this homework all SDLC phases will be covered and explained

##### Planning
As a part of this phase we will determine the form and a technical steck of our product.
Our product - thematical web service with dynamical contend display. All graphics is presented as a svg (scalable vector graphic), animated by open-source JS library - Vivus.
Product will be written on Go language. Distribution - docker container image. Further deployment - Kubernetes cluster.

#### Coding
0. IDE - Visual Studio Code.
1. Create working directory - _/html_, content - svg files, named after sequience (ex.frame1.svg)
2. Create source directory _/src_ - this directory stores source code of our web-server.
3. Create ***main.go*** file in _/src_ - create main function with cleent-server net/http protocol. Server listens to 8080 port on a local host (127.0.0.1), file server _./html_ - sorce of a static content. All requests on 8080 port will be forwarded to files in a current directory. 
4. Create _index.html_ file in _/html_ directory - now our server uses this page with the content as an index.
5. Use command ***go build -o bin/app src/main.go*** - create and compile our code in _bin/app_ directory, _src/main.go_ - our code stores here.
6. ***bin/app*** - command that runs our server. Open new terminal and use curl localhost:8080 to see the content of our web page and code of our index.html file.
#### Testing
Open browser and enter ***127.0.0.1:8080*** - browser displays the content of a slide (frame1.svg) stored in our _/html_ directory.
#### Delivery
1. Create _Dockerfile_ in our _/demo_ root directory - here we will store all instructions for our docker container 
2. ***go mod init demo*** commmand generates dependency file for our project in /src directory
3. In our project root directory use ***docker build .*** - start building our docker container
4. ***docker run -p 8080:8080 (our container)*** - now our project starts in isolated environment (container) on port 8080. Now it is available not only on our local machine, but for everyone
5. ***docker tag (container) ibayro/app:v1.0.0*** - assign name and path to our container and make it available for everyone, we will store it on DockerHub by default 
6. ***docker push ibayro/app:v1.0.0*** - download our image on our remote public profile
#### Deployment
1. ***k3d cluster create demo*** - create a cluster with nodes for our project.
2. ***kubectl create deploy demo --image ibayro/app:v1.0.0*** - deploy a pod with our project in it
3. ***kubectl get po -w*** - see the info about our pod
4. ***kubectl port-forward deploy/demo 8080*** - make port forwarding to our pod. Now our project runs not on a local machine, and not in our container, now we created a pod via kubernetes, it is a whole new level, we can now use all power of kubernetes (managing, logging, metrics, etc.)
#### Operations
1. Add new content by adding more frames.svg to our _/html_ directory, and build new docker image by assigning a new version of our project ***docker build -t ibayro/app:v1.0.1***
2. Push our newly upgraded version on DockerHub ***docker push docker.io/ibayro/app:v1.0.1***
3. Organize zero-downtime-deployment - updating new version of a pod without interrupting a service ***kubectl set image deploy demo app=ibayro/app:v1.0.1*** - kubernetes started pod upgrading process, new pod has been prepared and deployed, traffic has been switched on a new version only after working capacity check, older version of pod has been terminated afterward.

Now our homework is done, our project grew from a local machine availability to docker image, posted on DockerHub and further transformed into a kubernetes pod. 
