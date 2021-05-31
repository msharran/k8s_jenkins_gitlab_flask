# Gitlab minikube cluster in macOS using helm chart

_**Prerequisites**: Install helm, kubectl and minikube_

- Add gitlab helm repo

```bash
helm repo add gitlab https://charts.gitlab.io/
helm repo update 
```

- Fetch gitlab helm chart and save as values.yml

```bash
curl --output values.yaml "https://gitlab.com/gitlab-org/charts/gitlab/raw/master/examples/values-minikube-minimum.yaml"
```

- Get minikube ip using following cmd and update values.yaml file's line 14,15 

```bash
minikube ip
```

- Install gitlab

```bash
helm install gitlab -f values.yaml gitlab/gitlab
```


>Monitor the installation progress via `helm status gitlab` and `minikube dashboard`. The installation could take up to 20-30 minutes depending on the amount of resources on your workstation.

>When all the pods show either a Running or Completed status, get the GitLab password as described in Initial login, and log in to GitLab via the UI. It will be accessible via https://gitlab.domain where domain is the value provided in the values.yaml file **line 14**

---

## Root login

```bash
### Get root user password
kubectl get secret gitlab-gitlab-initial-root-password -ojsonpath='{.data.password}' | base64 --decode ; echo
```

Username: root

Password: `<obtained using previous command>`

Goto settings > general > Sign-up restrictions > Disable `Require admin approval for new sign-ups`

---

## User signup
1. Go to Register page and create a user using email `admin@sezzle.in`
2. give appropriate user name like `admin_sezzle`
3. give a password (eg, `gitlab@123!`) and signup
4. select the role like devOps engineer during first sign in
5. Thats it! you are in

---

**Results of my deployment:** Pls refer images in this directory (`admin@sezzle.in.png, gitlab-local.png`)

**Reference:** https://docs.gitlab.com/ee/administration/troubleshooting/kubernetes_cheat_sheet.html#installation-of-minimal-gitlab-configuration-via-minikube-on-macos