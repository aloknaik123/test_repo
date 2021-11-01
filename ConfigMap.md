# Sample Scenarios

This repo contains various practice questions for k8s configmaps.

## Questions

<details><summary>1a. Passing a ConfigMap entry to a container as an environment variable</summary>
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
        configMapKeyRef:
          name: <cm>
          key: <key name>
  ...
  ```
  </p>
</details>
    
<details><summary>1b. Passing a ConfigMap entry as a command-line argument</summary>
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
          configMapKeyRef:
            name: <cm>
            key: <key name>
      args: ["$(VARIABLE)"]
  ...
  ```
  </p>
</details>
    
<details><summary>2. Passing all entries of a ConfigMap as environment variables at once</summary>
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
      envFrom:
      - prefix: CONFIG_ (optional)
        configMapRef:
          name: <cm>
  ...
  ```
  </p>
</details>

<details><summary>3a. Using a configMap volume to expose ConfigMap entries as files</summary>
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
      ...
      - name: <volume name>
        mountPath: <mount path>
        readOnly: true
      ...
    volumnes:
    ...
    - name: <volume name>
      configMap:
        name: <cm>
    ...
  ...
  ```
  </p>
</details>
    
<details><summary>3b. Exposing certain ConfigMap entries in the volume</summary>
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
      ...
      - name: <volume name>
        mountPath: <mount path>
        readOnly: true
      ...
    volumnes:
    ...
    - name: <volume name>
      configMap:
        name: <cm>
        items:
        - key: <key-name>
          path: <new key-name>
    ...
  ...
  ```
  </p>
</details>

<details><summary>3c. Mounting individual ConfigMap entries as files without hiding other files in the directory</summary>
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
      ...
      - name: <volume name>
        mountPath: <mount path>/<new filename>
        subPath: <filename>
      ...
    volumnes:
    ...
    - name: <volume name>
      configMap:
        name: <cm>
        items:
        - key: <key-name>
          path: <new key-name>
    ...
  ...
  ```
  </p>
</details>

<details><summary>3d. Setting file permissions</summary>
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
      ...
      - name: <volume name>
        mountPath: <mount path>
        readOnly: true
      ...
    volumnes:
    ...
    - name: <volume name>
      configMap:
        name: <cm>
        defaultMode: "0660" # This sets the permissions for all files to -rw-rw----
    ...
  ...
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
