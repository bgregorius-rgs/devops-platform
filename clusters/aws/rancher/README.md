# Instructions

Configure Cert Manager for CloudFlare / LetsEncrypt integration

```
kubectl apply -f cert-manager.yaml
```
Delete old secret
```
kubectl delete secret -n cattle-system tls-rancher-ingress
```
Create new cert
```
kubectl create -f cert.yaml
```

Add additional ca secret:
```
kubectl -n cattle-system create secret generic tls-ca-additional --from-file=ca-additional.pem=./ca-additional.pem
```


Reconfigure Rancher to pull cert from secret
```
helm upgrade -f values.yaml rancher rancher-stable/rancher -n cattle-system
```
NOTE: This will take a few minutes to go through the certificate signing process with LetsEncrypt.



