<br>

## Setup Service Account

<br>

A service account should be created to allow chaosengine to run experiments in your application namespace.

**Apply the RBAC**

`kubectl apply -f https://litmuschaos.github.io/litmus/litmus-admin-rbac.yaml -n litmus`{{execute}}

<span style="color:green">**Expected Output**</span>

```bash
serviceaccount/litmus-admin created
clusterrole.rbac.authorization.k8s.io/litmus-admin created
clusterrolebinding.rbac.authorization.k8s.io/litmus-admin created
```
