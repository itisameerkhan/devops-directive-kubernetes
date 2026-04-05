# Built-in kubernetes resources

## How to use this section

- This section is meant to give you awareness of the different types of resources within Kubernetes and their use cases.

- We will revisit many of them in more detail in the context of the demo application later in the course.
- You should leave this section with a high level understanding of the building blocks, and that understanding will solidify as you actually use them in the following sections.

## Namespace

- Provides a mechanism to group resources within a cluster

- There are 4 initial namespaces: default, kube-system, kube-node-lease, kube-public
- 🚨 By default, namespaces DO NOT act as a network/security boundary
 

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: non-default
```

![deno](../assets/demo004.png)

### Creating Namespaces

```bash
kubectl create namespace ameer-ns
```

```bash
kubectl get namespace 
```

```cmd
NAME              STATUS   AGE
ameer-ns          Active   54s  👈
default           Active   29d
ingress-nginx     Active   21d
kube-node-lease   Active   29d
kube-public       Active   29d
kube-system       Active   29d
```

---


### creating namespace using yml

```yml
apiVersion: v1
kind: Namespace
metadata: 
    name: ameer-ns
```

```cmd
kubectl apply -f namespace.yml
```

```cmd
kubectl get namespace 
```

```cmd
NAME              STATUS   AGE
ameer-ns          Active   54s  👈
default           Active   29d
ingress-nginx     Active   21d
kube-node-lease   Active   29d
kube-public       Active   29d
kube-system       Active   29d
```

---

### deleting a namespace

```cmd
kubectl delete namespace ameer-ns
```

### deleting namespace using yml

```cmd
kubectl delete -f namespace.yml
```

---

## Pod

- The "smallest deployable unit"
- You will almost never create a pod directly (we are doing so only for educational purposes)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-minimal
spec:
  containers:
    - name: nginx
      image: nginx:1.26.0
```

## Pod 

```cmd
┌─────────────────────────────────────────────────────┐
│ Pod                                                  │
│                                                      │
│                        ┌───────────────────────┐    │
│                        │   Init Container(s)   │    │
│                        └───────────────────────┘    │
│  ┌──────────────────┐  ┌───────────────────────┐    │
│  │                  │  │                       │    │
│  │    Primary       │  │  Sidecar              │    │
│  │    Container     │  │  Container(s)         │    │
│  │                  │  │                       │    │
│  └──────────────────┘  └───────────────────────┘    │
│                                                      │
└─────────────────────────────────────────────────────┘
```
- A Pod can contain multiple containers

- Containers within a pod share networking and storage
- Init Containers
- Sidecar containers
- There are MANY more configurations available:
  - Listening ports

  - Health probes
  - Resource requests/limits
  - Security Context
  - Environment variables
  - Volumes
  - DNS Policies