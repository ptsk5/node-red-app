# Node-RED IBM Cloud Starter Application (modification)

## Usage

Final image is stored here: `quay.io/jpetnik/node-red-app-ic:latest`

In order to deploy into the K8s:

- Copy `cloudant.Secret.yaml.template` into `cloudant.Secret.yaml`.
- In the `cloudant.Secret.yaml` file, fill in your cloudant service credentials (as a single line).
- Log into the K8s cluster.
- Apply yamls by: `kubectl apply -f k8s/`

## Build

```bash
docker build --platform=linux/amd64 -t quay.io/jpetnik/node-red-app-ic .
docker push quay.io/jpetnik/node-red-app-ic:latest
```
