CI / CD Architecture:

![WhatsApp Image 2020-12-14 at 02 56 08](https://user-images.githubusercontent.com/31888672/102708845-307a5b80-42ae-11eb-8351-7dfa9dd10f9d.jpeg)

Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

This repo will deploy the ArgoCD components and a definition of your app for ArgoCD to watch and sync.

- Tag namespaces with istio-injection=enabled lable:

<pre><code>

kubectl label namespace NAMESPACE istio-injection=enabled

</code></pre>


- Deploy: 

<pre><code>

kubectl apply -f argocd-manifest.yaml

</code></pre>

1. Access UI by Istio GW

Here you will see the magic of ArgoCD by expecting the pipeline that your deployment has 
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

kubectl -n app get all # in this case the deployment will be in the app namespace as per the config in kubernetes-manifests/

</code></pre>

2. Check your rollout: 

<pre><code>

kubectl argo rollouts get rollout istio-rollout --watch

</code></pre>
