CI part:
 1. Build the docker image from dockerfile( go based web app)
 2. Code quality check (using golangci-lint)
 3. Docker image is pushed to Dockerhub
 4. based on the tag on the dockerimage in dockerhub the 'tag' in vaules.yaml of helm chart will be updated 
CD part:
  ArgoCD will watch for any change in CI, if yes then it will be deployed to k8s cluster

Challenges I faced:
1. make sure the approriate golangci version is set
2. make sure the GITHUB TOKEN ( secrets.TOKEN) has appropriate permission to write/update tag in values.yaml of helm-chart
