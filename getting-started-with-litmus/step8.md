<br>

## Observe and Verify Chaos

<br>

**Observe the Chaos results**

<br>

<span style="color:green">ChaosResult CR name will be `<chaos-engine-name>-<chaos-experiment-name>`</span>

`kubectl describe chaosresult nginx-chaos-pod-delete -n litmus`{{execute}}

Describe the ChaosResult CR to know the status of each experiment. The `status.verdict` is set to `Awaited` when the experiment is in progress, eventually changing to either `Pass` or `Fail`.

<br>

> If you receive an `Error from server (NotFound): chaosresults.litmuschaos.io "nginx-chaos-pod-delete" not found` response from the server, wait for a minutes and try again. It takes a little bit of time for the Chaos Engine to run.

<span style="color:green">**Expected Output:**</span>

```bash
Name:         nginx-chaos-pod-delete
Namespace:    litmus
Labels:       app.kubernetes.io/component=experiment-job
              app.kubernetes.io/part-of=litmus
              app.kubernetes.io/version=3.20.0
              batch.kubernetes.io/controller-uid=f18519e9-aa62-4e4c-9cb9-733cf144b4ef
              batch.kubernetes.io/job-name=pod-delete-wjy03k
              chaosUID=58094bcf-14d4-4d8b-bc78-3c2241715610
              controller-uid=f18519e9-aa62-4e4c-9cb9-733cf144b4ef
              job-name=pod-delete-wjy03k
              name=pod-delete
Annotations:  <none>
API Version:  litmuschaos.io/v1alpha1
Kind:         ChaosResult
Metadata:
  Creation Timestamp:  2025-09-06T11:54:12Z
  Generation:          2
  Resource Version:    5670
  UID:                 0100ea32-6f62-4424-a842-f5f1576bdd40
Spec:
  Engine:      nginx-chaos
  Experiment:  pod-delete
Status:
  Experiment Status:
    Phase:                     Completed
    Probe Success Percentage:  100
    Verdict:                   Pass
  History:
    Failed Runs:   0
    Passed Runs:   1
    Stopped Runs:  0
    Targets:
      Chaos Status:  targeted
      Kind:          deployment
      Name:          nginx
Events:
  Type    Reason   Age   From                     Message
  ----    ------   ----  ----                     -------
  Normal  Awaited  108s  pod-delete-wjy03k-rm74m  experiment: pod-delete, Result: Awaited
  Normal  Pass     68s   pod-delete-wjy03k-rm74m  experiment: pod-delete, Result: Pass
```

<br>

_Incase you want to try running chaos on a separate image or namespace, check out the [official documentation](https://docs.litmuschaos.io/docs/getstarted/) and get your chaos experiments up and running in minutes_

<br>
