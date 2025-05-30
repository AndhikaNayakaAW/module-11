# Module 11
## Andhika Nayaka Arya Wibowo - 2306174135

## Reflection: Hello Minikube Tutorial

### 1. Application Logs Before and After Service Exposure

Before exposing the pod as a service, the logs showed a one-time startup message indicating that the HTTP and UDP servers were started:

![Startup Logs](module-11/img/sslogs.png)

After exposing the pod and accessing the app via `minikube service hello-node`, the logs updated **each time I opened the URL** in the browser. This indicates that every page visit triggers an HTTP request handled by the pod, confirming that the service routing works properly.

![After Exposure Logs](module-11/img/ss1.png)

Additionally, this combined view shows how the log evolves from just a startup message to multiple `GET /` events:

![Explained Logs](module-11/img/ss2.png)

---

### 2. Understanding `kubectl get` vs `kubectl get -n kube-system`

The `kubectl get` command without the `-n` option lists resources in the **default namespace**, where my `hello-node` deployment and pod were created.

On the other hand, `kubectl get pods -n kube-system` lists resources in the **kube-system namespace**, which includes internal components like DNS, the metrics-server, and the Kubernetes dashboard itself.

That's why I didn’t see my app in the `kube-system` namespace — user deployments and system services are logically separated into different namespaces. This helps in isolating workloads and managing access.

---

### 3. Kubernetes Dashboard Overview

This is the dashboard showing the status of my deployment, pod, and replicaset — all running properly:

![Kubernetes Dashboard](module-11/img/dashboard.png)

---

### 4. Summary

This tutorial helped me understand:
- How to run a local Kubernetes cluster with Minikube
- Deploy containers using `kubectl`
- Use services to expose pods to the outside world
- Monitor the system with the Kubernetes Dashboard and `kubectl`
- The concept and practical usage of namespaces in Kubernetes

---