This repo is used to setup and control a kubernetes running on Azure Kubernetes Service and leveraging GitOps workflows to peform neccasary actions.

Brief Summary of the contents:
Workflows contains 2 workflows that both end in the same result. 'Auto' automatically starts the process when the folder 'first' is pushed to. The 'GitOps' allows you to manually enter a acr and repo to build the image to.

Appcode just contains basic html webpage I used to test updates. This is essentially my 'app' image that my K8 is running.

First contains the yaml file that my ArgoCD monitors for changes which it will then pull to my cluster

Dockerfile is what the workflow uses to build image off

app.yaml was the file I used to initally setup my argocd on my k8 cluster

The steps to replicate are as follows...

Let's start with azure, I'll assume you have an account setup:
1. Create a resource group.

2. Create a kubernetes cluster, you can change the parameter names and VM model as you need. I chose to have 1 node and a cheap VM to reduce costs.
    $ az aks create `
    --resource-group Test `
    --name akstest `
    --location eastus `
    --node-count 1 `
    --load-balancer-sku basic `
    --node-vm-size "Standard_B2s_v2" `
    --generate-ssh-keys

3. Install kubectl on the AKBS.
    https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/

4. Install ArgoCD to your AKBS.
    https://foxutech.medium.com/setup-argocd-on-azure-kubernetes-services-9c3fa543f4b6

5. Create a container registry and repository
    Type 'container registries' into the search bar and hit 'create'
    Inside your new container registry, create a repository.

And GitHub:
6. Follow instructions 1 - 5 on this page to set up a connection between Azure and GitHub
    https://github.com/Azure/aks-baseline-automation/blob/main/workloads/docs/app-flask-push-dockerbuild.md
