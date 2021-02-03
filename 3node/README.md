This file is the same as a standard installation, with the exception of the worker replica count is set to 0.

Once you’ve created the install-config.yaml file, run the openshift-install create manifests command in the same directory as the install-config.yaml file. You’ll see the following output:

```
$ openshift-install create manifests
INFO Consuming Install Config from target directory
WARNING Making control-plane schedulable by setting MastersSchedulable to true for Scheduler cluster settings
```

Note the message about marking masters as schedulable. This message signifies that you will be installing a three-node cluster where the masters will also act as workers. Verify this by taking a look at the scheduling manifest.Note the message about marking masters as schedulable. This message signifies that you will be installing a three-node cluster where the masters will also act as workers. Verify this by taking a look at the scheduling manifest.

```
$ cat manifests/cluster-scheduler-02-config.yml
apiVersion: config.openshift.io/v1
kind: Scheduler
metadata:
  creationTimestamp: null
  name: cluster
spec:
  mastersSchedulable: true
  policy:
name: ""
status: {}
```


