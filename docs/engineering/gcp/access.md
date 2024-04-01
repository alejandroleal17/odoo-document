# Access to the Platform

This guide provides the necessary information to access the Navigator Platform on the GCP (Google Cloud Platform) side. Please ensure you have everything needed from the list below.

## Requirements

- **OpenVPN Client**: Download it from [here](https://openvpn.net/client/).
- **OpenVPN Access**: During the onboarding process, you should have been provided with a file (e.g., `username.ovpn`). Make sure you import this file into the VPN client.
- **gcloud** CLI: In case you want to access the Kuberneetes cluster. Download it from [here](https://cloud.google.com/sdk/gcloud)
- [gke-gcloud-auth-plugin](https://cloud.google.com/blog/products/containers-kubernetes/kubectl-auth-changes-in-gke): Kubectl requires it to use GCP credentials for accessing the cluster. Please check the latest documentation for installation. As of the current date, it involves executing the following command: gcloud components install gke-gcloud-auth-plugin

## Development Environment

### Connecting to the Cluster (a.k.a *troc-cluster-dev*)

You must have the gcloud CLI installed and configured with your username. Set the context with the cluster using the following command:

```shell
$ gcloud container clusters get-credentials navigator-platform --region us-west1 --project troc-cluster-dev
```
