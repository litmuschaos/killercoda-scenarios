<br>

## Prepare ChaosEngine

<br>

**Check the current number of the Pods**

<br>

You would only be able to see the `nginx` pod in running state.

`kubectl get pods`{{execute}}

<span style="color:green">**Expected Output:**</span>

```
nginx-86c57db685-vd8k6   1/1     Running   0         <TimeStamp>
```

<br>

**Explore the ChaosEngine yaml**

ChaosEngine connects the application instance to a Chaos Experiment.

Explore the ChaosEngine yaml [https://hub.litmuschaos.io/generic/pod-delete](https://hub.litmuschaos.io/generic/pod-delete)

## Run Chaos

<br>

**Apply the ChaosEngine manifest to trigger the experiment.**

Create the following ChaosEngine spec.

```
cat <<EOF > engine.yaml
apiVersion: litmuschaos.io/v1alpha1
kind: ChaosEngine
metadata:
  name: nginx-chaos
  namespace: litmus
spec:
  appinfo:
    appns: 'default'
    applabel: 'app=nginx'
    appkind: 'deployment'
  annotationCheck: 'true'
  engineState: 'active'
  chaosServiceAccount: litmus-admin
  monitoring: false
  experiments:
    - name: pod-delete
      spec:
        components:
          env:
            # set chaos duration (in sec) as desired
            - name: TOTAL_CHAOS_DURATION
              value: '30'

            # set chaos interval (in sec) as desired
            - name: CHAOS_INTERVAL
              value: '10'

            # pod failures without '--force' & default terminationGrace>
            - name: FORCE
              value: 'false'

             ## percentage of total pods to target
            - name: PODS_AFFECTED_PERC
              value: ''
EOF
```{{execute}}

Apply the `engine.yaml` file :

`kubectl apply -f engine.yaml`{{execute}}

<span style="color:green">**Expected Output:**</span>

```bash
chaosengine.litmuschaos.io/nginx-chaos created
```

<br>

**Check the health of the Pod**

<br>

You would be able to see that two new pods in the `litmus` ns

`kubectl get pods -n litmus`{{execute}}

-   `nginx-chaos-runner`
-   `pod-delete-<hash>`

would be created and age would be the latest time stamp. 

If you watch for the nginx pod now, you'd be able to see the pod getting recreated as the experiment proceeds.

`watch -n 1 kubectl get pod`{{execute}}

<span style="color:green">**Expected Output:**</span>

```
NAME                     READY   STATUS              RESTARTS   AGE
nginx-5869d7778c-npr5n   0/1     Completed           0          73s
nginx-5869d7778c-rfsmr   0/1     ContainerCreating   0          0s
```

In the `litmus` namespace once the expirement is over you should see the pod-delete experiment pod cvhange status to `Completed`.

`watch -n 1 kubectl get pods -n litmus`{{execute}}

<span style="color:green">**Expected Output:**</span>

```
nginx-chaos-runner        0/1     Completed     0          <TimeStamp>
pod-delete-tkwb3x-9g789   0/1     Completed   0          <TimeStamp>
```
