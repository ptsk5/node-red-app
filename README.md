# Node-RED IBM Cloud Starter Application (modification)

## Build

```bash
docker build --platform=linux/amd64 -t quay.io/jpetnik/node-red-app-ic .
docker push quay.io/jpetnik/node-red-app-ic:latest
```

## Run locally (from code)

```bash
export CLOUDANT_URL="https://hostname"
export CLOUDANT_APIKEY="apikeyvalue"

npm i
npm start
```

## Run locally (Docker)

```bash
export CLOUDANT_URL="https://hostname"
export CLOUDANT_APIKEY="apikeyvalue"

docker run -it --rm -p 3000:3000 -e CLOUDANT_URL=$CLOUDANT_URL -e CLOUDANT_APIKEY=$CLOUDANT_APIKEY quay.io/jpetnik/node-red-app-ic:latest
```

## Run in K8s / OCP cluster

Steps:

- Copy `k8s/cloudant.Secret.yaml.template` into `k8s/cloudant.Secret.yaml`.
- In the `k8s/cloudant.Secret.yaml` file, fill in your cloudant service credentials (`CLOUDANT_URL` only, or including `CLOUDANT_APIKEY`).
- Log into the K8s/OCP cluster.
- Apply yamls by: `kubectl apply -f k8s/`

**Disclaimer**: Since this repository mainly targets a deployment to the free Kubernetes service in IBM cloud, the service is of the `NodePort` type.

## Environment variables

Among other defaults (node-red specific variables), this repository adds the following envs:

| Name              | Description                                                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `CLOUDANT_URL`    | Cloudant url. Set "https://hostname" for IAM authentication or "https://username:password@hostname" for basic authentication. |
| `CLOUDANT_APIKEY` | IAM apiKey. Set "apikey value" for IAM authentication. Or use "" or do not set this variable at all for basic authentication. |
