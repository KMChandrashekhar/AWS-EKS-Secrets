# aws-eks-secret-csi-demo


### Lets Understand what is Secrets Store CSI Driver

```
The Secrets Store CSI Driver secrets-store.csi.k8s.io allows Kubernetes to mount multiple secrets, keys,
and certs stored in enterprise-grade external secrets stores into their pods as a volume.
Once the Volume is attached, the data in it is mounted into the container's file system.
```

### Install CSI drivers


# Secrets Store CSI Secret driver.

```
helm repo add secrets-store-csi-driver \
  https://kubernetes-sigs.github.io/secrets-store-csi-driver/charts
```

```
helm install -n kube-system csi-secrets-store \
  --set syncSecret.enabled=true \
  --set enableSecretRotation=true \
  --set rotationPollInterval=15s \
  secrets-store-csi-driver/secrets-store-csi-driver
```

# AWS Secrets and Configuration Provider

```
kubectl apply -f https://raw.githubusercontent.com/aws/secrets-store-csi-driver-provider-aws/main/deployment/aws-provider-installer.yaml
```

# Verify the installations

```
kubectl get daemonsets -n kube-system -l app=csi-secrets-store-provider-aws
kubectl get daemonsets -n kube-system -l app.kubernetes.io/instance=csi-secrets-store
```


### Create an IAM OIDC identity provider for your cluster.

```
eksctl utils associate-iam-oidc-provider --cluster secret-csi-cluster  --approve --region us-east-2
```
