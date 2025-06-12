# Services
Expose an application running in your cluster behind a single outward-facing endpoint, even when the workload is split across multiple backends.

## Syntax

```
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: NodePort / ClusterIP / LoadBalancer
  selector:
    app.kubernetes.io/name: MyApp
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9376
    - name: https
      protocol: TCP
      port: 443
      targetPort: 9377
```

## Types of Services 

### ClusterIP
- Exposes the Service on a cluster-internal IP. Choosing this value makes the Service only reachable from within the cluster. 
- This is the default that is used if you don't explicitly specify a type for a Service. You can expose the Service to the public internet using an Ingress or a Gateway.


### NodePort
- Exposes the Service on each Node's IP at a static port (the NodePort). 
- To make the node port available, Kubernetes sets up a cluster IP address, the same as if you had requested a Service of type: ClusterIP.
- This helps to expose the application to outside world.

### LoadBalancer
- This is used to integrate a built-in load balancer by various cloud platforms like GCP, AWS and Azure. 
- If this set in any platform that is not supported, it will act as Nodeport without custom configuration capabilities.


