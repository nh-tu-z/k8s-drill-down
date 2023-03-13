## Deploy a Resilient Node.js Application on Kubernetes From Scratch

Reference: [link](https://www.digitalocean.com/community/tech-talks/how-to-deploy-a-resilient-node-js-application-on-kubernetes-from-scratch)


### Run k8s in local env

1. Install Docker desktop (Windows)
2. Enable `Kubernetes` in Settings of Docker desktop
3. Run PowerShell and run a test command such as `kubectl get pods` 

### Some command to investigate the deployment file

1. Check the result after apply the `.yaml` file
    ```shell
    # Get deployments
    kubectl get deployments

    # Get nodes
    kubectl get nodes -o wide

    # Get pods
    kubectl get pods

    # Metadata details of pod
    # First list pods
    kubectl get pods
    # Get metadata based on pod name
    kubectl describe pods <pod-name>
    ```

TODO - write deployment, service

TODO - include some kubectl to monitor the app