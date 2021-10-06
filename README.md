# GET STARTED

The helm charts using deploy openvpn server on k8s cluster. The helm chart supports ldap authentication.

In the lab, I use `glauth`  is ldap lightweight servers.

# Using

``` shell

git clone https://github.com/helm-openvpn-docker-ldap.git

cd helm-openvpn-docker-ldap
# Create new namepsace
kubectl create ns openvpn
helm -n openvpn install . openvpn

```

# Configuration

Edit file values.yaml to customize openvpn server.

# Generate new config for openvpn

``` shell
KEY_NAME="trungn"
SERVICE_IP="10.10.10.10"

kubectl --namespace openvpn exec -it "$POD_NAME" /etc/openvpn/setup/newClientCert.sh "$KEY_NAME" "$SERVICE_IP"
kubectl --namespace openvpn exec -it "$POD_NAME" cat "/etc/openvpn/certs/pki/$KEY_NAME.ovpn" > "$KEY_NAME.ovpn"
```

# Reference

- https://github.com/helm/charts/tree/master/stable/openvpn
- https://github.com/trungng1992/openvpn-docker-ldap-auth