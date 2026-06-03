## The instruction to validate the changes
1. Running the cluster:
```bash
kind create cluster --config cluster.yml
```
2. Use manifests:
```bash
kubectl apply -f security/rbac.yaml
kubectl apply -f deployment.yaml
```
3. Checking the access to the secret from pod:
```bash
kubectl exec -it <NAME_OF_POD> -- curl -s [https://kubernetes.default.svc/api/v1/namespaces/default/secrets](https://kubernetes.default.svc/api/v1/namespaces/default/secrets) --cacert /var/run/secrets/kubernetes.io/serviceaccount/ca.crt -H "Authorization: Bearer $(cat /var/run/secrets/kubernetes.io/serviceaccount/token)"
```
4. 