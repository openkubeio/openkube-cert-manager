### Overview

cert-manager is a native Kubernetes certificate management controller. It can help with issuing certificates from a variety of sources, such as Let’s Encrypt, HashiCorp Vault, Venafi, a simple signing key pair, or self signed.

It will ensure certificates are valid and up to date, and attempt to renew certificates at a configured time before expiry.


### Documentation

>https://cert-manager.io/docs/installation/kubernetes/

>https://cert-manager.io/docs/configuration/


### Stable Release
>https://github.com/jetstack/cert-manager/releases/tag/v1.2.0


### Installation

Apply the below cert-manager yaml to create the cert-manager crd and resources. Take a quick look into the 
yaml to view the resources
>https://github.com/jetstack/cert-manager/releases/download/v1.2.0/cert-manager.yaml


Installing with regular manifests
```
kubectl create namespace cert-manager
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.2.0/cert-manager.yaml
kubectl get pods -n cert-manager
```



### Configuration

In order to configure cert-manager to begin issuing certificates, first Issuer or ClusterIssuer resources must be created. These resources represent a particular signing authority and detail how the certificate requests are going to be honored.

Supported Issuer Types

- SelfSigned
- CA
- Vault
- Venafi
- External
- ACME





