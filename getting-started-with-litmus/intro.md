<br>

<h1 align="center">
  <img src="https://raw.githubusercontent.com/litmuschaos/website-litmuschaos/staging/src/images/LitmusLogo.png" alt="LitmusChaos" width="200">
</h1>

<br>

## **Getting Started with Litmus** 😮😎

Litmus is a toolset to do cloud-native chaos engineering. Litmus provides tools to orchestrate chaos on Kubernetes to help SREs find weaknesses in their deployments. SREs use Litmus to run chaos experiments initially in the staging environment and eventually in production to find bugs, vulnerabilities. Fixing the weaknesses leads to increased resilience of the system.

<br>

---

<br>
Litmus takes a cloud-native approach to create, manage and monitor chaos. Chaos is orchestrated using the following Kubernetes Custom Resource Definitions (CRDs):

-   **ChaosEngine**: A resource to link a Kubernetes application or Kubernetes node to a ChaosExperiment. ChaosEngine is watched by Litmus' Chaos-Operator which then invokes Chaos-Experiments
-   **ChaosExperiment**: A resource to group the configuration parameters of a chaos experiment. ChaosExperiment CRs are created by the operator when experiments are invoked by ChaosEngine.
-   **ChaosResult**: A resource to hold the results of a chaos-experiment. The Chaos-exporter reads the results and exports the metrics into a configured Prometheus server.

## **You should use Litmus because:**

-   Litmus provides chaos CRDs to manage chaos. Using chaos API, orchestration, scheduling and complex workflow management can be done declaratively.
-   Most of the generic chaos experiments are readily available for you to get started with your initial chaos engineering needs.
-   SDK is available in GO, Python and Ansible. A basic experiment structure is created quickly using SDK and developers and SREs just need to add the chaos logic into to make a new experiment.
-   Simple to complex chaos workflows are easy to construct. Use GitOps and the chaos workflows to scale your chaos engineering efforts and increase the resilience of your Kubernetes platform.

## **In this scenario you will learn how to:**

-   Setup and install Litmus onto Kubernetes.
-   Install Litmus experiments, RBAC and prepare the Chaos Engine.
-   Deliver chaos experiments.
-   Observe the chaos engine exercise your experiments.

## **Run your first chaos experiment** 📹

<br>

[!<img src = 'https://i.ibb.co/1sB5hwY/maxresdefault.jpg' width='400'/>](https://youtu.be/W5hmNbaYPfM)

<br>
