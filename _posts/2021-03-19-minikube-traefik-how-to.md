---
title: "Minikube + Traefik: How to"
date: 2021-03-19T00:00:00+10:00
categories:
  - blog
tags:
  - kubernetes
  - minikube
  - traefik
  - devops
---

# Minikube + Traefik: How to

I have a target system with a pre-configured [Traefik](https://traefik.io) ingress controller.
I would like to do my development locally, and that means setting up my laptop to have much 
the same components. I already have
[Minikube](https://minikube.io) installed, so I wanted to install Traefik, to make things
as similar as possible.

## Why do we need this guide?

For whatever reason, the documentation I found was either incomplete, or out-of-date, or 
occasionally just plain wrong. So 
this guide is a one-stop-shop for myself if I ever need to set these things up again.

For instance, the official instructions say to use the minikube ingress add-on, but from what 
I can tell, that results in everything using the minikube nginx ingress controller and not
Traefik at all. At the very least, I could not get such a system using the Traefik controller.

## Guide starts here:

### Prerequisites

The usual suspects:
* Minikube to install kubernetes (I'm using 1.18.10 but I don't think that's important here)
* Helm
* kubectl

Nice to have:
* k9s       (because who wants to type `kubectl` commands repetitively?)

### Start and configure minikube
```shell
minikube start
minikube addons enable metallb  #  A bare-metal load balancer
minikube ip                     #  Take note of this address. In my case I got 192.168.64.12
minikube addons config metallb  #  I set the address range to 192.168.64.100 - 192.168.64.200 
```

Check that the resulting config looks correct:
```shell
<your shell prompt here>➜ kubectl -n metallb-system describe configmap

Name:         config
Namespace:    metallb-system
Labels:       <none>
Annotations:  <none>

Data
====
config:
----
address-pools:
- name: default
  protocol: layer2
  addresses:
  - 192.168.64.100-192.168.64.200

Events:  <none>
```
If the address range doesn't come up, try disabling and re-enabling the metallb addon.

### Install Traefik using helm
```shell
helm repo add traefik https://containous.github.io/traefik-helm-chart
helm install traefik traefik/traefik
```
You will be able to see that the `traefik...` LoadBalancer service in the `default` namespace
has a valid External-IP - in my case 192.168.64.100.

I got Traefik version 2.2.8 using this helm chart. Your mileage may vary.

### Specify an Ingress for a service
I won't go in to how to set up deployments and services, but here is a working Ingress
specification:
```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: traefik-test
  namespace: traefik-test
  annotations:
    kubernetes.io/ingress.class: traefik
spec:
  rules:
  - http:
      paths:
      - path: /hello
        backend:
          serviceName: test-app
          servicePort: 8080
```
Note that I had tried some other `annotations` but they didn't work with my system.

Make sure that your service is a `NodePort`.

Finally, you should be able to go to your browser and navigate to the expected address:
in my case it's at http://192.168.64.100/hello

## Summary

We have brought up a kubernetes cluster using Minikube, and set up Traefik as an 
ingress controller, using the metallb loadbalancer. I have also shown a minimal
working ingress specification for our system.

* It's an exercise for the reader to set up SSL certs for https termination of this system!