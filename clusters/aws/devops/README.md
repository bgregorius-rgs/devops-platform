# Manual Instructions
```
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
```
```
helm upgrade -i devops-cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values.yaml
```s