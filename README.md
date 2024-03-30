This is the repo I use to control my k8 cluster on azure.

1. Workflows contains 2 workflows that both end in the same result. 'Auto' automatically starts the process when the folder 'first' is pushed to. The 'GitOps' allows you to manually enter a acr and repo to build the image to.

2. Appcode just contains basic html webpage I used to test updates

3. First contains the yaml file that my argocd monitors for changes to pull

4. Dockerfile is what the workflow uses to build image off

5. app.yaml was the file I used to initally setup my argocd on my k8 cluster
