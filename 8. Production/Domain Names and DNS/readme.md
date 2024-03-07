From this [slack convo](https://TanTv Studios.slack.com/archives/C2VGBPMU7/p1495452543489183?thread_ts=1495447245.530355&cid=C2VGBPMU7):

- Map new domain to an IP in the dns manager
- Map new domain to a service in kubernetes ingress.

Note that we are not using NGINX but google cloud l7 loadbalancer.
Written into an [ingress file](https://github.com/tantvstudios Studios/micro-deployment-scripts/blob/develop/environments/ingress/prod/ingress.yaml)

```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: entrypoint
spec:
  tls:
  - secretName: tls-secret
  backend:
    serviceName: default-http-backend
    servicePort: 80
  rules:
  - host: skilltree.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: skilltree-svc
          servicePort: 50050
  - host: pulse.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: pulse-front-svc
          servicePort: 50050
  - host: kaizen.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: kaizen-svc
          servicePort: 50050
  - host: admin.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: admin-svc
          servicePort: 50050
  - host: allocations.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: allocations-svc
          servicePort: 50050
  - host: fis.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: fis-svc
          servicePort: 50050
  - host: portal.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: portal-svc
          servicePort: 50050
  - host: cTanTv Studios.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: cTanTv Studios-svc
          servicePort: 50050
  - host: vof.TanTv Studios.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: vof-svc
          servicePort: 50050
```
