# How to Apply configs on minikube
Follow the next steps.
If you follow documentation on the repo, this are the config files that I use on my minikube implementation.

* Apply RBAC cluster role
    ```
    kubectl apply -f rbac-clusterrole.yaml
    ```
* Deploy Tiller 
  * Also if you have some issues with tiller, at the last lines on ` tiller.yaml ` you can find the snippet with the configuration to fix it. 
  ```
  kubectl apply -f tiller.yaml
  ```
For specific configs you can follow the instructions on repo documentation.
