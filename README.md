## More About Me – [Take a Look!](http://www.mjakaria.me)

### GitOps

GitOps is a DevOps practice where Git repositories serve as the single source of truth for defining and managing infrastructure and application deployments, with automated systems continuously syncing the actual environment to the desired state stored in Git.

### ArgoCD

Argo CD is a declarative, GitOps-based continuous delivery tool for Kubernetes that automatically deploys and synchronizes applications from Git repositories to clusters, ensuring the live state matches the desired state defined in Git.

#### ArgoCD Install & Configuration

```bash
kubectl create namespace argocd
kubectl apply -n argocd \
  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get pods -n argocd
kubectl port-forward svc/argocd-server -n argocd 8085:443
https://localhost:8085
```

##### Get Admin Password

```bash
kubectl get secret argocd-initial-admin-secret \
  -n argocd \
  -o jsonpath="{.data.password}" | base64 --decode
```

> Login:

- Username: `admin`
- Password: `output from above`

#### Install Argo CD CLI - Optional but Recommended

```bash
brew install argocd
argocd version
```

#### Login via CLI

```bash
argocd login localhost:8085 \
  --username admin \
  --password Tg5v7O0J6ImlDpJd \
  --insecure
```

#### Expose Argo CD via NodePort (instead of port-forward) - Optional

```bash
kubectl patch svc argocd-server -n argocd \
  -p '{"spec": {"type": "NodePort"}}'
```

```bash
kubectl patch svc argocd-server -n argocd \
-p '{"spec": {"type": "LoadBalancer"}}'
```

```bash
minikube service argocd-server -n argocd # Get URL
```

## With Regards, `Jakir`

[![LinkedIn][linkedin-shield-jakir]][linkedin-url-jakir]
[![Facebook-Page][facebook-shield-jakir]][facebook-url-jakir]
[![Youtube][youtube-shield-jakir]][youtube-url-jakir]

### Wishing you a wonderful day! Keep in touch

<!-- Personal profile -->

[linkedin-shield-jakir]: https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-url-jakir]: https://www.linkedin.com/in/jakir-ruet/
[facebook-shield-jakir]: https://img.shields.io/badge/Facebook-%231877F2.svg?style=for-the-badge&logo=Facebook&logoColor=white
[facebook-url-jakir]: https://www.facebook.com/jakir.ruet/
[youtube-shield-jakir]: https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white
[youtube-url-jakir]: https://www.youtube.com/@mjakaria-ruet/featured
