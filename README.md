# 9Spokes DevSecOps Challenge

## Overview

Welcome to the 9Spokes DevSecOps technical challenge! We value and appreciate the diversity and uniqueness of thought in each individual. It is our intent is to learn more about you via the code you write and your approach to solving problems.

This repo contains the instructions and the data you need to complete the _9Spokes DevSecOps Challenge_. This challenge is not intended to be complex, but it is an opportunity for you to showcase your understanding and applying of good infrastructure & basic development practices. We strongly value the _Infrastructure as Code_ approach to managing Cloud resources, hence we encourage you to think about the repeatability of your exercise using a _config-driven_ approach to infrastructure.

You are encouraged to treat this as a real-life project. This typically means:

-   Use version control effectively
-   Include some basic documentation if applicable
-   Use a proper naming convention that suits you

Once you are done, please share your work by submitting a public link to your repository. Include any special notes or running instructions in a README.md file of your choice.

Try not to exceed 2-3 hours on this exercise.

## The Challenge

### Docker

This repo contains a sample _hello world_ application written in Go in the `hello/` directory. The first phase of this challenge is to build this application into a Docker container using the supplied `Dockerfile`. You will need to push the resulting image to a Docker registry of your choice. The image will be used in subsequent steps.

-   🤓 [Image pushed into Dockerhub](https://hub.docker.com/r/tinahmgao/go-hello)

### Kubernetes

-   Create a Kubernetes cluster using any method you'd like (e.g. `kops`, `minikube`, `microk8s` or Cloud)
-   Create a new `namespace` called `staging`.

---

-   🤓 I choose minikube in this challenge
-   📁 I created namespace with the `staging.yml`

---

### Single Pod

-   Create a new `pod` called `hello` in this `staging` namespace, make sure it is in a _healthy_ state. Use the `hello` image from the step above for this task.

---

-   🧐 I set `readinessProbe - httpGet` to make sure the pod is in healthy state
-   ❓ As I run minikube on MacOS, I need to use the `minikube tunnel` to reach the pod, but I failed in such way. [I found similar issue as this Open issue of Minikube](https://www.notion.so/9spokes-devsecops-challenge-ef26b63478494e46a49d3cc345d16bb0#7766584eb72c4f8b9e6932d56cb19b4b)
-   📁 `singlepod.yml`

---

### Multi-node

-   Assume you are operating a 3 node (`node-1`, `node-2`, and `node-3`) cluster, deploy a `pod` called `p2` in every `node` of your cluster.

---

-   🧐 I use `podAntiAffinity` to make sure the pods are deployed evenly among nodes
-   📁 `multinode.yml`

---

### Multi-container Pod

-   Create a new `pod` called `p3` in the `staging` namespace. This `pod` contains two containers and the `pod` only should be created when one of these two containers has a file called `/app/ready.txt`. The `pod` should fail if that container does not have that file.

---

-   🧐 I set `readinessProbe - exec` to check container files
-   📁 `multicontainer.yml`

---

### Monitoring

-   Deploy _prometheus_ alert manager and _grafana_ into the `kube-system` namespace and configure customised alerts called `9spokes-cpu-alert` which is only going to be trigger when a `pod` has **80%** of the CPU running for 60 seconds. You should send the details of this alert with your name into Microsoft Teams Channel located [here](https://9spokes.webhook.office.com/webhookb2/42d60780-c647-4a13-867d-0a273bff104b@2abcc5bb-97a6-431e-aa58-27c540baed73/IncomingWebhook/6200cfc5fd3744cf9838be6cb70194f3/ef4e28f0-b9f1-4169-8320-2a70d372596c).
-   Deploy an `ingress` controller to protect _prometheus_ and _alert manager_ using any authentication method you'd like.

---

-   🧐 I've found some resources, need more time to complete the task.

---

**Thank you and good luck!**
