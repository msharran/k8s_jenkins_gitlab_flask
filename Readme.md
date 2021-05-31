# Flask + Gitlab + Jenkins deployments in k8s cluster

_**Prerequisites**: Install helm, kubectl and minikube_

_**Note**: I used macOS_

---

### To start Minikube

```bash
minikube start --cpus 3 --memory 12000 #Needed for gitlab
minikube addons enable metrics-server
minikube addons enable ingress 
```

---

1. You can find Dockerized flask demo server under ./flask_demo_dockerized
2. Please find below, the links to each Readme files

    1. [Flask Demo Deployment](./k8s_config.d/flask_demo_deployment/)

    2. [Gitlab Deployment](./k8s_config.d/gitlab_deployment/)

    3. [Jenkins Deployment](./k8s_config.d/jenkins_deployment/)

---