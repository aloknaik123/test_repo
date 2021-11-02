# Code Snippets

This repo contains code snippets of k8s secrets.

## as environment variable
<details><summary>1. Injecting secrets into environment variables</summary>
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
      env:
      - name: VARIABLE
        valueFrom:
          secretKeyRef:
            name: <secret-name>
            key: <key name>
  ...
  ```
  </p>
</details>
    
## as files
<details><summary>2. Using a secret volume to project secret entries into files</summary>
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
        readOnly: true
    volumes:
    - name: <vol-name>
      secret:
        secretName: <secret-name>
        items:
        - key: <key-name>
          path: <file name>
          mode: 0600 (optional)
  ...
  ```
  </p>
</details>
