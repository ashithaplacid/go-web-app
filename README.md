CI part:
 1. Build the docker image from multi-stage dockerfile( go based web app)
 2. Code quality check (using golangci-lint)
 3. Docker image is pushed to Dockerhub
 4. based on the tag on the dockerimage in dockerhub the 'tag' in vaules.yaml of helm chart will be updated 
CD part:
  ArgoCD will watch for any change in CI, if yes then it will be deployed to k8s cluster

Challenges I faced:
1. make sure the approriate golangci version is set
2. make sure the GITHUB TOKEN ( secrets.TOKEN) has appropriate permission to write/update tag in values.yaml of helm-chart


I have initially deployed the k8s in EKS without and with helm chart before implementing it through CI to make sure everything is working fine.
I have used nginx ingress controller so that the web app was able to be exposed to outside world through LB in EKS cluster
