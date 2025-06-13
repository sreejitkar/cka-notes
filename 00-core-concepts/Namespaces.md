# Namespaces
- Namespaces in k8s are like houses where each resource related to the same concern are associated with.
- By default, kubernetes creates its own namespace for storing its own resources like kube-system and kube-public.
- Each namespace can have its own policies and allowed resource limits.
- If one resource ones wants to refer to a resource in a different service, it can do so using the folllowing format.
```
resource-name.namespace.resource-type.domain
```
For example `db-service.dev.svc.cluster.local`

- Namespace can be specified in any resource definition under the metadata section.
- `ResourceQouta` can be used to limit resources for an namespace.
