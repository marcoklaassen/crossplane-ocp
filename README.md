# Crossplane Demo installed on Red Hat OpenShift managing AWS infrastructure

## Installation

```
helm install crossplane \
    crossplane-stable/crossplane \
    --set securityContextCrossplane.runAsUser=null \
    --set securityContextCrossplane.runAsGroup=null \
    --set securityContextRBACManager.runAsUser=null \
    --set securityContextRBACManager.runAsGroup=null \
    --namespace crossplane-system \
    --create-namespace
```

## Create the AWS Secret
```
oc create secret generic aws-secret --from-file=creds=./aws-credentials.txt
```

## Install Ressources 

```
oc apply -f provider-config.yaml
oc apply -f controller-config.yaml
oc apply -f provider.yaml
```

## Create your first bucket

```
oc create -f bucket.yaml
```

