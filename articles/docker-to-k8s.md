Getting started with Kubernetes deployments

This article is a "spiritual" continuation of a [Jenkins 2.0 tutorial I authored](https://github.com/iflowfor8hours/jenkins2-pipeline-demo) and the [CoreOS Kubernetes tutorial](https://coreos.com/kubernetes/docs/latest/kubernetes-on-vagrant-single.html). It assumes that you have a single node cluster setup and running on your local machine. If you would like to follow along, follow the instructions from the [CoreOS Documentation](https://coreos.com/kubernetes/docs/latest/kubernetes-on-vagrant-single.html). Otherwise, the intention of this article is to get the reader familiar with Kubernetes concepts and where to start in deploying an application to a cluster and how to get value out of using kubernetes locally.

I have a stateless [java spring boot application](https://github.com/iflowfor8hours/sample-spring-cloud-svc-ci) that I want to move to a Kubernetes cluster with the goal of making it both fault tolerant and cloud-agnostic. I currently can build and test it locally, and it runs just fine inside a docker container as well, as evidenced by deploying it to Pivotal Cloud.

The source for most of this information has been from the [Kubernetes Config Best Practices guide](http://kubernetes.io/docs/user-guide/config-best-practices/) and the [Kubernetes Documentation](http://kubernetes.io/docs)

The first step is to define a Kubernetes service for the application. A service is a named load balancer that proxies traffic to one or more containers. When initially creating a service, you need to define it and then feed it to the Kubernetes API. The file below is an example service definition file `sample-app-service.yaml` for our web application.

```
apiVersion: v1                                                                        
kind: Service
metadata:
  name: sample-application
  labels:
    app: sample-application
spec:
  ports:
  - port: 8080
    targetPort: 8080
  selector:
    app: sample-application
```

After creating this file, run the following to deploy it to Kubernetes

```
$ kubectl create -f sample-app-service.yaml 
service "sample-application" created
```

Now you should be able to see your service by executing `kubectl get svc` to show that it is exists.

Next, we need to create a deployment for our application. A deployment is responsible for managing multiple instances of a replicated pod. The Deployment will automatically launch new pods if the number of replicas falls below the specified number. We will use this here to deploy multiple instances of our application for redundancy and availability. In production, we would deploy these across multiple kubernetes minions.

```
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: sample-application
  labels:
    app: sample-application
spec:
  replicas: 3
  selector:
    matchLabels:
      app: sample-application
  template:
    metadata:
      labels:
        app: sample-application
    spec:
      containers:
      - name: java-8
        image: gcr.io/google-samples/gb-frontend:v4
        resources:
          requests:
            cpu: 100m
            memory: 100Mi
        env:
        - name: GET_HOSTS_FROM
          value: dns
        ports:
				- name: http-server
          containerPort: 80
```

I want to mimic the current setup that I had in CloudFoundry from the previous demo which was a jenkins server that is watching changes, then deploying to a number of environments.



The background of this is that I had a java spring boot application that I wanted to learn how to move it to a Kubernetes cluster. 


Quick introduction to CD

What is CD?

What are the advantages of CD?


