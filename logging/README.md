# Cluster Logging

The following commands will deploy cluster logging components on OpenShift. See also the [Logging documentation](https://docs.openshift.com/container-platform/latest/logging/cluster-logging.html).

## Deploying the standard EFK stack

```
$ oc apply --kustomize elasticsearch-operator/base
```

```
$ oc apply --kustomize cluster-logging-operator/base
```

# Deploying OpenShift logging

To deploy cluster logging for development purposes, run this command:

```
$ oc apply --kustomize cluster-logging-instance/overlays/development
```

To deploy cluster logging to production, run this command:

```
$ oc apply --kustomize cluster-logging-instance/overlays/production
```

To deploy cluster logging to only forward logs to an external fluentd/logstash:

```
$ oc apply --kustomize cluster-logging-instance/overlays/log-forwarding-only
```

## Deploying Event Router

Refer to [Working with Event Router](https://docs.openshift.com/container-platform/4.3/logging/cluster-logging-eventrouter.html) for more information.

```
$ oc process -f event-router/event-router-template.yaml | oc apply --filename -
```
