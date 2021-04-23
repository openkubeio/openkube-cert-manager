
### Example Issuer Types SelfSigned**

Create a self-signed Issuer

Create a Certificate assign it to a secret

```
kubectl apply -f hotel.yaml
kubectl get all --namespace hotel
kubectl get certificate -n hotel
kubectl describe certificate -n hotel
```