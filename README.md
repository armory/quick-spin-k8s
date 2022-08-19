# quick-spin-k8s

quick-spin-k8s is a simple way to run Armory Spinnaker in Kubernetes.

## Requirements

quick-spin-k8s is a list of k8s manifest files which can be applied to any Kubernetes environment e.g. EKS, GKS, Kind, k3s, k3d, minikube and others.

Linux distribution

* 2 vCPUs (recommend 4)
* 8GiB of RAM (recommend 16)
* 30GiB of HDD (recommend 40+)

## Installation

1. Setup and configure kubectl.
2. Execute the commands in your terminal:

    ```bash
    kubectl apply -f service-account.yaml
    kubectl apply -f mysql.yaml
    kubectl apply -f redis.yaml
    kubectl apply -f .
    ```

## Accessing Spinnaker

1. Forward ports for Gate and Desk services:

    ```bash
    kubectl -n spinnaker port-forward svc/spin-deck 9000:9000
    kubectl -n spinnaker port-forward svc/spin-gate 8084:8084
    ```

2. Go to http://localhost:9000

## Uninstall

Execute the command in your terminal:

```bash
kubectl delete -f .
```

## Troubleshooting

If your environment doesn't meet the minimal requirements then clouddriver, front50, orca, and gate services will not be able to get up.
You can try to increase `startupProbe.initialDelaySeconds` to solve this issue.
