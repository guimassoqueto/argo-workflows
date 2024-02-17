
1. Init minikube
   ```shell
   minikube start
   ```

2. Create a new namespace named "argo" in Kubernetes
    ```shell
    kubectl create namespace argo
    ```

3. Apply a YAML file from a remote location to the Kubernetes cluster in the argo namespace. In this case, it applies the quick-start-minimal.yaml file from the specified GitHub release of the Argo Workflows project.
    ```shell
    kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v3.5.4/quick-start-minimal.yaml
    ```

4. Set up a port forwarding connection using kubectl in the context of the Argo project
```shell
kubectl -n argo port-forward deployment/argo-server 2746:2746
```

5. Submit an Argo workflow for execution and monitor its progress
```shell
argo submit -n argo --watch <github-raw-yaml-file>
```

Open the Program on [localhost:2746](https://localhost:2746) to see the workflows