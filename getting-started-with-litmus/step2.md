<br>

## Apply the LitmuChaos Operator manifest

<br>

```bash
helm repo add litmuschaos https://litmuschaos.github.io/litmus-helm/

kubectl create ns litmus

helm install chaos litmuschaos/litmus-core --namespace=litmus
```{{execute}}

The above command installs all the CRDs, required service account configuration, and chaos-operator.

<span style="color:green">**Expected Output**</span>

```bash
"litmuschaos" has been added to your repositories

namespace/litmus created

NAME: chaos
LAST DEPLOYED: Sat Sep  6 11:35:27 2025
NAMESPACE: litmus
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
## Additional Steps (Verification)
----------------------------------
You can run the following commands if you wish to verify if all desired components are installed successfully.

- Check if chaos api-resources are available: 

root@demo:~# kubectl api-resources | grep litmus 
chaosengines                                   litmuschaos.io                 true         ChaosEngine
chaosexperiments                               litmuschaos.io                 true         ChaosExperiment
chaosresults                                   litmuschaos.io                 true         ChaosResult

- Check if the litmus chaos operator deployment is running successfully

root@demo:~# kubectl get pods -n litmus 
NAME                      READY   STATUS    RESTARTS   AGE
litmus-7d998b6568-nnlcd   1/1     Running   0          106s

## Start Running Chaos Experiments 
----------------------------------
With this, you are good to go!! Refer to the chaos experiment documentation @ https://docs.litmuschaos.io 
to start executing your first experiment.
```

Check the available namespaces and see if `litmus` is present or not

`kubectl get namespaces`{{execute}}

You should be able to see litmus as an active namespace that you just created.
