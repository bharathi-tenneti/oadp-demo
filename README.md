# oadp-demo
How to take backup and restore using OADP operator in Redhat Openshift , using Openshift Data Foundations(ODF) as storage backend.

## Pre-Reqs
1. Red Hat Openshift cluster.
2. ODF , OADP operators installed.

## Usecase
Deploy a full stack maria db application with a nodejs front end, and a python backend servcie talking with MariaDB.
Use OADP to take backups using ODF Nooba Storage class.

## MariaDB Application setup 
Find the turorial here to setup full stack application [here](https://developers.redhat.com/learning/learn:openshift:learn-kubernetes-using-developer-sandbox/resource/resources:set-your-activity-environment)

## Create mariadb application stack, including the front end and backend apps.
```
oc new-project mariadb
oc create -f apps/manifests/mariadb/quotd-python
oc create -f apps/manifests/mariadb/quotessql
oc create -f apps/manifests/mariadb/quoesweb
```

Git repos for the source code
https://github.com/bharathi-tenneti/quotesweb.git
https://github.com/bharathi-tenneti/quotemysql.git
https://github.com/bharathi-tenneti/qotd-python.git

# Create ObjectBucketClaim, and backup yamls. This should create an objectBucket in ODF storage, DataProtectionApplication Instance, and a backup instance created to backup "mariadb"  namespace.


```
oc create -f obc.yaml
oc create -f dpa.yaml
oc create -f backup.yaml
```

# Time to test: Go ahead and delete mariadb namespace, and restore it using below yaml. You should see all the apps running in the mariadb namespace
```
oc create -f restore.yaml
```

