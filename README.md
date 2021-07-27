# Aaron Cutchin / Bitpusher Test Helm Chart Repo

* Based on [this tutorial](https://medium.com/@mattiaperi/create-a-public-helm-chart-repository-with-github-pages-49b180dbb417)

##  Procedures

### Create New Helm Chart from Template

    helm create helm-chart-sources/<chart_name>

### Lint All Charts

    helm lint helm-chart-sources/*

### Package All Charts

    helm package helm-chart-sources/*

### Create/Update Repo Index (index.yaml)

    helm repo index --url `cat repo.url` .

### Update Repo Index with New Charts

    helm repo index --url `cat repo.url` --merge index.yaml .

### Add This Repo to Your Local Helm Repo Cache

    helm repo add ac-bp-helm-charts `cat repo.url`

### Search Local Helm Repo Cache for "test" Chart

    helm search repo test

### Handy multi-command command lines

    helm lint helm-chart-sources/* && helm package helm-chart-sources/* && helm repo index --url `cat repo.url` .

    git add -A && git commit -m 'test helm chart update' && git push

    helm repo update && helm search repo ac-bp-helm-charts

