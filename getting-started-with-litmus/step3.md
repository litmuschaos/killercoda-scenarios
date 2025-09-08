<br>

## Verifying the Litmus Installation

<br>

**Verify if the chaos operator is running**

`kubectl get pods -n litmus`{{execute}}

<span style="color:green">**Expected Output:**<span>

```bash
litmus-<numericId>-<id> 1/1 Running 0
```

**Verify if chaos CRDs are installed**

`kubectl get crds | grep chaos`{{execute}}

<span style="color:green">**Expected Output:**</span>

```bash
chaosengines.litmuschaos.io <Creation Timestamp>

chaosexperiments.litmuschaos.io <Creation Timestamp>

chaosresults.litmuschaos.io <Creation Timestamp>
```

**Verify if the chaos api resources are successfully created in the desired (application) namespace**

`kubectl api-resources | grep chaos`{{execute}}

<span style="color:green">**Expected Output:**</span>

```bash
chaosengines litmuschaos.io true ChaosEngine

chaosexperiments litmuschaos.io true ChaosExperiment

chaosresults litmuschaos.io true ChaosResult
```
