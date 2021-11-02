# Code Snippets

This repo contains code snippets of k8s downwardAPI.

## as environment variable
<details><summary>1a. Injecting POD object fields into environment variables</summary>
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
      - name: POD_NAME
        valueFrom:
          fieldRef:
            fieldPath: metadata.name
      - name: POD_IP
        valueFrom:
          fieldRef:
            fieldPath: metadata.podIP
      - name: NODE_NAME
        valueFrom:
          fieldRef:
            fieldPath: metadata.nodeName
      - name: NODE_IP
        valueFrom:
          fieldRef:
            fieldPath: metadata.hostIP
  ...
  ```
  </p>
</details>

<details><summary>1a. Injecting CONTAINER resource fields into environment variables</summary>
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
      - name: MAX_CPU_CORES
        valueFrom:
          resourceFieldRef:
            resource: limits.cpu
      - name: MAX_MEMORY_KB
        valueFrom:
          resourceFieldRef:
            resource: limits.memory
            divisor: 1k
  ...
  ```
  </p>
</details>
    
## as files
<details><summary>2. Using a downwardAPI volume to expose pod metadata as files</summary>
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
      downwardAPI:
        items:
        - path: </path/to/file>
          fieldRef:
            fieldPath: metadata.name
  ...
  ```
  </p>
</details>
