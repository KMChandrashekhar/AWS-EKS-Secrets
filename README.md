# AWS-EKS-Secrets
How to use Secret Store CSI Driver with AWS EKS Cluster ( AWS Secrets Manager )

Lets Understand what is Secrets Store CSI Driver
The Secrets Store CSI Driver secrets-store.csi.k8s.io allows Kubernetes to mount multiple secrets, keys,
and certs stored in enterprise-grade external secrets stores into their pods as a volume.
Once the Volume is attached, the data in it is mounted into the container's file system.
Install CSI drivers
Secrets Store CSI Secret driver.
helm repo add secrets-store-csi-driver \
  https://kubernetes-sigs.github.io/secrets-store-csi-driver/charts
