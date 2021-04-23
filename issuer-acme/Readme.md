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
**Renewing your certificate**

By default, Let’s Encrypt certificates expire every 90 days. Let’s Encrypt usually sends an e-mail (like the one above) to the address associated with the Certificate resource created in Kubernetes to remind the cluster admin to renew it. 

- Check certificate status
  ```
  kubectl describe certificates le-crt -n cottage
  ```
- Delete the Certificate and Secret
  ```
  kubectl delete certificate le-crt  -n cottage
  kubectl delete secret tls-lets-secret -n cottage
  ```
- Re-create the certificate in Kubernetes
  ```
  kubectl apply -f cottage-certificate-definition.yml
  ```
- Verify the new expiry dates
  ```
  kubectl describe certificates le-crt -n cottage
  ```

To keep with DevOps principles, we shouldn’t have to be running the above steps manually every time 
rather let’s put it all together into a handy-dandy script: ***renew-cert.sh***

  
