# Setup-Kubernetes-dashboard-on-k8s

This template will help you to setup kubernetes dashboard along with metric-scrapper.

## Install dashboard and metric scrapper

To install dashboard running below command on a kubernetes cluster.

        kubectl apply -f namespace.yml
        kubectl apply -f ../setup-kubernetes-dashboard-on-k8s/

After applying the above files now run below command to view dashboard

        kubectl proxy

and visit to this page

        http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login


## Get token to login to dashboard

To get secret run below commad

        kubectl get secret -n kubernetes dashboard

Now, you will see bunch of secret now you to pick one with the name admin-user-token-*****

After this get this secret in yaml format

        kubectl get secret admin-user-token-***** -n kubernetes-dashboard -o yaml

Now get the value of token, and decode it from base64

        echo <token-value> | base64 -d