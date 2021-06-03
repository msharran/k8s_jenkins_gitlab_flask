# Jenkins minikube cluster using helm chart

_**Prerequisites**: Install helm, kubectl and minikube_

- Create jenkins namespace
```bash
kubectl apply -f jenkins-namespace.yaml
```

- Create a dedicated volume in local system for dev purpose
```bash
kubectl apply -f jenkins-volume.yaml
```

- Add jenkins helm repo
```bash
helm repo add stable https://charts.helm.sh/stable
helm repo update 
```

- Install jenkins deployment
```bash
helm install jenkins-release -f values.yaml stable/jenkins --namespace jenkins
```
- Get root user password saved in values.yaml
```bash
printf $(kubectl get secret --namespace jenkins jenkins-release -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
 ```

- Port forward to http://127.0.0.1:8080
```bash
export POD_NAME=$(kubectl get pods --namespace jenkins -l "app.kubernetes.io/component=jenkins-master" -l "app.kubernetes.io/instance=jenkins-release" -o jsonpath="{.items[0].metadata.name}")
echo http://127.0.0.1:8080
kubectl --namespace jenkins port-forward $POD_NAME 8080:8080
```

_**Notes**: It may take time depending on your system configuration_

---

## Admin Login

Username: admin@sezzle.in

Password: jenkins@123!
