## Deploy a Resilient Node.js Application on Kubernetes From Scratch

Reference: [link](https://www.digitalocean.com/community/tech-talks/how-to-deploy-a-resilient-node-js-application-on-kubernetes-from-scratch)

### Install K8s in local machine

1. We must have a hypervisor have been installed in the local machine as a pre-ccondition to run `Minikube` which is based to run `kubectl`. Hypervisor should be the `Hyper-V` or `VirtualBox`. `Hyper-V` is the best choice for Windows. And `VirtualBox` is great if you need something call **cross-platform**. At the time, I write this article, I am using Win 10 so I choose `Hyper-V`. Reference link [here](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)

2. Install `Minikube` and start it follow this [link](https://minikube.sigs.k8s.io/docs/drivers/hyperv/). Run PowerShell as administrator and run the command:
    ```shell
    minikube start --driver=hyperv 
    ```

3. Run some samples `kubectl` command to check whether it works

### Run k8s in local env using Docker (test not successfully)

1. Install Docker desktop (Windows)
2. Enable `Kubernetes` in Settings of Docker desktop
3. Run PowerShell and run a test command such as `kubectl get pods` 

### Namespace

1. There are 4 default namespaces: `default`, `kube-node-lease`, `kube-public` and `kube-system`

2. View available namespaces
    ```shell
    kubectl get namespace
    ```
    or 
    ```shell
    kubectl get namespaces --show-labels
    ```

3. Create a namespace
    ```shell
    kubectl create -f ./k8s/np/proj-np.yaml
    ```

4. Delete a namespace
    ```shell
    kubectl delete namespaces <insert-some-namespace-name>

    # Example
    kubectl delete namespaces tuhngo-namespace
    ```

### Nodes

### Some command to investigate the deployment file

1. Check the result after apply the `.yaml` file (this result might be used to input of investigation)
    ```shell
    # Get deployments
    kubectl get deployments

    # Get nodes
    kubectl get nodes -o wide

    # Get pods
    kubectl get pods

    # Metadata details of pod
    kubectl get pods # First list pods
    kubectl describe pods <pod-name> # Get metadata based on pod name
    ```

TODO - write deployment, service

TODO - include some kubectl to monitor the app

### References

1. K8s Cheat sheet - [link](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
2. Exit code in Container & K8s - [link](https://komodor.com/learn/exit-codes-in-containers-and-kubernetes-the-complete-guide/)
3. Config various `minikube` drivers - [link](https://minikube.sigs.k8s.io/docs/drivers/)