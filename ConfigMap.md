# Sample Scenarios

This repo contains various practice questions for k8s configmaps.

## Questions

<details><summary>1. Passing a ConfigMap entry to a container as an environment variable</summary>
  <p>
    
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: <pod-name>
  spec:
    containers:
    - image: <image-name>
      env:
      - name: VARIABLE
        valueFrom:
        configMapKeyRef:
          name: <cm>
          key: <key name>
  ```
  </p>
  </details>

<details><summary>2. give scenario detail here</summary>
  <p>
    
  ```
  kubectl get pv
  ```
  </p>
  </details>
