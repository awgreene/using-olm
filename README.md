# Run OLM in OpenShift/Minishift
## Prereq
1. Be a cluster admin
2. Have an OpenShift/MiniShift cluster running
3. For Optional Step: Have git installed
## OPTIONAL: Use Operator Lifecycle Manager (OLM) toolkit to generate olm templates
```bash
git clone https://github.com/operator-framework/operator-lifecycle-manager
cd operator-lifecycle-manager
./scripts/package-release.sh 1.0.0-localolm ../self-generated-olm-templates ../olm-configuration.yaml
cd ../
```

## Create a sandbox and deploy olm operators
```bash
oc new-project olm-sandbox
oc apply -f olm-templates 
```

## Create a sandbox, define the JBoss CRD, and deploy JBoss operator
```bash
oc new-project sandbox
oc create -f setup-olm/jboss-operator/jboss-crd.yaml
oc create -f setup-olm/jboss-operator/deploy-jboss-operator.yaml
```

