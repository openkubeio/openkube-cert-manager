### Example Issuer Types ACME

The ACME Issuer type represents a single account registered with the Automated Certificate Management Environment (ACME) Certificate Authority server. 
<br/><br/>Certificates issued by public ACME servers are typically trusted by client’s computers by default. This means that, for example, visiting a website that is backed by an ACME certificate issued for that URL, will be trusted by default by most client’s web browsers. ACME certificates are typically free


**Creating a Basic ACME Issuer**
- Create a acme Issuer with lets Encrypt
- Create a certificate with lets Encrypt isssuer
- apply the yaml

```
kubectl apply -f farmvilla.yaml
kubectl get all --namespace farmvilla
kubectl get certificate -n farmvilla
kubectl describe certificate -n farmvilla
```