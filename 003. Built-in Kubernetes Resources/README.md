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