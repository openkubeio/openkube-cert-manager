### Example Issuer Types CA

Create a self signed CA Certificate
- **Create Root Key**

    openssl genrsa -des3 -out certs/ca.key 4096

- **Create and self sign the Root Certificate**

    openssl req -x509 -new -nodes -key certs/ca.key -sha256 -days 1024 -out certs/ca.crt -subj "/C=US/ST=CA/O=OpenKube/CN=app.openkube.io"

Create a namespace and pack the ca in a tls secret


```
kubectl create ns resort

cat <<EOF | kubectl apply -f - 
apiVersion: v1
kind: Secret
metadata:
  name: ca-key-pair
  namespace: resort
data:
  tls.crt: $(cat certs/CA.crt | base64 -w0)
  tls.key: $(cat certs/CA.key | base64 -w0)
EOF

```

Apply the yaml to create Issuer and certificate signed with the custom ca
```
kubectl apply -f resort.yaml
```