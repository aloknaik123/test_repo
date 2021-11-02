# Code Snippets

This repo contains code snippets of k8s downwardAPI.

## as files
<details><summary>1. Using a projected volume in a pod</summary>
  <p>
    
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: <pod-name>
  spec:
    containers:
    - image: <image-name>
      name: <container-name>
      volumeMounts:
      - name: <vol-name>
        mountPath: </path/to/dir>
    volumes:
    - name: <vol-name>
      projected:
        sources:
        - configMap:
            name: <cm>
        - secret:
            name: <secret name>
            items:
            - key: <key name>
              path: <file name>
  ...
  ```
  </p>
</details>
