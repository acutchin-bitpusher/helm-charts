# Aaron Cutchin / Bitpusher Test Helm Chart Repo

* Based on [this tutorial](https://medium.com/@mattiaperi/create-a-public-helm-chart-repository-with-github-pages-49b180dbb417)

##  Procedure

1. Create or Modify Helm Chart

  * New Chart from Template

            helm create helm-chart-sources/<chart_name>

  * Or modify existing chart under helm-chart-sources/
     * NOTE: When modifying a Helm chart, remember to increment version: in Chart.yaml

1. Lint All Charts

        helm lint helm-chart-sources/*

1. Package All Charts

        helm package helm-chart-sources/*

1. Create/Update Repo Index (index.yaml)

        helm repo index --url `cat repo.url` .

1. Update Repo Index with New Charts

        helm repo index --url `cat repo.url` --merge index.yaml .

1. Add This Repo to Your Local Helm Repo Cache

        helm repo add ac-bp-helm-charts `cat repo.url`

1. Git add/commit/push

1. Configure local Helm Repo Cache

  1. Add helm repo (if necessary)

            helm repo add ac-bp-helm-charts https://acutchin-bitpusher.github.io/helm-charts/

  1. Update helm repo (such as after updating a chart version)

            helm repo update && helm search repo ac-bp-helm-charts

      * NOTE: You will likely have to repeat the above command for a few minutes until the most recent chart versions are cached locally


### Search Local Helm Repo Cache for "test" Chart

    helm search repo test

### Handy multi-command command lines

    helm lint helm-chart-sources/* && helm package helm-chart-sources/* && helm repo index --url `cat repo.url` .

    git add -A && git commit -m 'test helm chart update' && git push

    helm repo update && helm search repo ac-bp-helm-charts

