We will install the Bookinfo application inside its own namespace and allow Istio to automatically inject the Sidecar Proxy.

<pre><code>

kubectl create namespace bookinfo
kubectl label namespace bookinfo istio-injection=enabled

</code></pre>


Deploy the application

<pre><code>

kubectl -n bookinfo apply -f bookinfo.yaml
kubectl -n bookinfo get pod,svc

</code></pre>

Create an Istio Gateway

<pre><code>

kubectl -n bookinfo apply -f gateway.yaml

# Check url: https://bookinfo-app.team-liran.ml/productpage
You will see that the service points via round robin to 3 pod versions

</code></pre>

Istio Feature:

1. Create the default destination rules

<pre><code>

kubectl -n bookinfo apply -f destination-rule-all.yaml

# This will give us the ability to choose to which pod route the trafic on the service side

</code></pre>

2. Route traffic to one version of a service

<pre><code>

kubectl -n bookinfo apply -f virtual-service-all-v1.yaml

</code></pre>

3. Route based on user identity

<pre><code>

kubectl -n bookinfo apply -f virtual-service-reviews-test-v2.yaml

# To test:
# Click Sign in from the top right corner of the page.
# Log in using jason as user name with a blank password.
</code></pre>

4. Traffic Shifting

<pre><code>

kubectl -n bookinfo apply -f virtual-service-reviews-50-v3.yaml

</code></pre>