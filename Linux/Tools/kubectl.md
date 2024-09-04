kubectl Notes
=============

* Documenting learning kubectl and Kubernetes. For more information on Kubernetes itself, see my [Intro to DevOps and SRE notes](https://github.com/CiscoSteve42/Notes/blob/main/Linux/LFCA/IntrotoDevOps.md).

* I'll also be learning minikube, my first goal is to just get a basic Jellyfin container up and running on my laptop as a practical first project.

### Setting up kubectl and minikube

* On Arch, I was able to get both of these packages using pacman. refer to documentation for your distro for installation instructions.

* Make sure that kubectl is configured to use minikube's cluster `kubectl config use-context minikube`

* Run a .yaml file to create and deploy with `kubectl apply -f filename.yaml` with filename being the name of the yaml

* Access URL for the service with `minikube service nameof-service --url`

* Check pods with `kubectl get pods`, similar to `docker ps` with Docker

* `helm` is the package manager for K8s

* To launch the Web-UI using minikube, use `minikube dashboard`

* Like Docker, you can use `kubectl exec -ti yourservice-42069 /bin/sh` to get a shell for your container 

* Also like Docker, you can check logs with `kubectl logs -f yourservice-42069`

* The equivalent of `docker rm` is `kubectl delete`
