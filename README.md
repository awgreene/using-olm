# Run OLM in Minishift
## Prereq
Make sure to copy this file to the operator-lifecycle-manager repo.
## Create a sandbox to host olms
```
$ oc new-project olm-sandbox
```
## Build deployment resources for an olm cluster
```
$ ./scripts/package-release.sh 1.0.0-localolm ./local-olm setup-olm/olm-configuration.yaml
```
## Create OLM operators
```
$ oc apply -f local-olm/templates 
```
## Create a sandbox for JBoss operator
```
$ oc new-project sandbox
```
## Define CustomResourceDefinition for JBoss
```
$ oc create -f setup-olm/jboss-operator/jboss-crd.yaml
```
## Deploy JBoss operator in the Sandbox
```
$ oc create -f setup-olm/jboss-operator/deploy-jboss-operator.yaml
```

