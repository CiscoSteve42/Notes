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
