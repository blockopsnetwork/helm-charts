<!--
DO NOT EDIT README.md manually!
We're using [helm-docs](https://github.com/norwoodj/helm-docs) to render values of the chart.
If you updated values.yaml file make sure to render a new README.md locally before submitting a Pull Request.

If you're using [pre-commit](https://pre-commit.com/) make sure to install the hooks first:
```
pre-commit install
```
REAMDE.md will be updating automatically after that.

Otherwise, you should install helm-docs and manually update README.md. Navigate to repository root and run:
`helm-docs --chart-search-root=charts/testnet-manager --template-files=README.md.gotmpl`

You may encounter `files were modified by this hook` error after updating README.md.gotmpl file when using pre-commit.
This is intended behaviour. Make sure to run `git add -A` once again to stage changes in the auto-updated REAMDE.md
-->

# Testnet Manager Helm chart

The helm chart installs the [Testnet Manager](https://github.com/paritytech/testnet-manager).

![Version: 1.3.2](https://img.shields.io/badge/Version-1.3.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Parity | <devops+helm@parity.io> | <https://github.com/paritytech/helm-charts> |

## Installing the chart

```console
helm repo add parity https://paritytech.github.io/helm-charts/
helm install testnet-manager parity/testnet-manager
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| args | object | `{"server":["-m","gunicorn","-k","uvicorn.workers.UvicornWorker","main:app","--bind=0.0.0.0:5000","--timeout=3600","--capture-output","--enable-stdio-inheritance","--workers=4"],"taskScheduler":["-m","gunicorn","-k","uvicorn.workers.UvicornWorker","task-scheduler:app","--bind=0.0.0.0:5000","--timeout=3600","--capture-output","--enable-stdio-inheritance","--workers=1"]}` | Configuration of validator-manager. This is a YAML-formatted file. Declare variables to be passed into your templates. |
| externalValidators | list | `[]` | Configuration of external validators |
| extraEnv | list | `[]` | Extra Environment variables |
| extraLabels | list | `[]` | Additional common labels on pods and services |
| fullnameOverride | string | `""` | Provide a name to substitute for the full names of resources |
| image | object | `{"pullPolicy":"IfNotPresent","repository":"paritytech/testnet-manager","tag":"latest"}` | Image of the main container |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy |
| image.repository | string | `"paritytech/testnet-manager"` | Image repository |
| image.tag | string | `"latest"` | Image tag |
| imagePullSecrets | list | `[]` | Reference to one or more secrets to be used when pulling images. ref: https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/ |
| ingress | object | `{"enabled":false}` | Creates an ingress resource |
| ingress.enabled | bool | `false` | Enable creation of Ingress |
| nameOverride | string | `""` | Provide a name in place of node for `app:` labels |
| nodeSelector | object | `{}` | Define which Nodes the Pods are scheduled on |
| podAnnotations | object | `{}` | Annotations to assign to the Pods |
| podSecurityContext | object | `{}` | SecurityContext holds pod-level security attributes and common container settings. ref: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/ |
| replicaCount | int | `1` | Replicas count |
| resources | object | `{"limits":{"cpu":2,"memory":"2Gi"},"requests":{"cpu":"500m","memory":"128Mi"}}` | Resource limits & requests |
| resources.limits.cpu | int | `2` | CPU resource limits |
| resources.limits.memory | string | `"2Gi"` | Memory resource limits |
| resources.requests.cpu | string | `"500m"` | CPU resource requests |
| resources.requests.memory | string | `"128Mi"` | Memory resource requests |
| securityContext | object | `{}` | SecurityContext settings for the main container |
| service | object | `{"port":80,"type":"ClusterIP"}` | Configure parameters of the Service |
| service.port | int | `80` | Exposed Service port |
| service.type | string | `"ClusterIP"` | Service type |
| serviceAccount | object | `{"annotations":{},"create":true,"name":""}` | Service account to use. |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
