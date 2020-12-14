Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

This repo will deploy the ArgoCD components and a definition of your app for ArgoCD to watch and sync.

- Deploy: 

<pre><code>

kubectl apply -f production/

</code></pre>

1. Access UI by Istio GW

Here you will see the magic of ArgoCD by expecting the pipeline that your canary-app.yaml deployment has 
created. 

- Error inspection
- Yaml inspection
- Sync inspection
- Pipeline review
- Status review
- And more!

- Default username: admin
- Get the password: 

<pre><code>

kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2

</code></pre>

2. Check your deployment: 

<pre><code>

kubectl -n app get all # in this case the deployment will be in the app namespace as per the config in production/

</code></pre>