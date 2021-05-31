# Flask minikube cluster in macOS


_**Prerequisites**: Install kubectl and minikube_

- Create flaskdemo namespace
```bash
kubectl apply -f flaskdemo-namespace.yml
```

- Deploy flaskdemo k8s cluster

```bash
kubectl apply -f flaskdemo-deployment.yml --namespace flaskdemo
```

- Expose the external service to the internet using minikube

```bash
minikube service flaskdemo-service -n flaskdemo
```
---

>Note: Flask image is hosted in my [DockerHub](https://hub.docker.com/r/sharran/flaskdemo) account