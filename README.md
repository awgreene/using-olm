# Run Operators using  OLM in OpenShift
## Prerequisites
1. Have an OpenShift cluster with Operator Lifecycle Manager [installed](https://github.com/operator-framework/operator-lifecycle-manager/blob/master/Documentation/install/install.md).
2. Be logged in as a user with the RBAC permissions required to deploy this operator. These RBAC permissions are currently undefined, so log in as a user with the Cluster Admin Role.

## Create a sandbox for the operators deployed by the OLM
```bash
$ oc new-project sandbox
```

## Define the JBoss CRD, and deploy JBoss operator
```bash
$ oc create -f example-operators/jboss/jboss-crd.yaml
$ oc create -f example-operators/jboss/jboss-operator-csv.yaml
```

## Define the echo CRD, deploy echo operator, and deploy an echo-app
```bash
$ oc create -f example-operators/echo/echo-crd.yaml
$ oc create -f example-operators/echo/echo-operator-csv.yaml
$ oc create -f example-operators/echo/deploy-echo-container.yaml
```
