# oadp-demo
How to take backup and restore using OADP operator in Redhat Openshift , using Openshift Data Foundations(ODF) as storage backend.

## Pre-Reqs
1. Red Hat Openshift cluster.
2. ODF , OADP operators installed.

## Usecase
Deploy a full stack maria db application with a nodejs front end, and a pythin backend servcie talking with MariaDB.
Use OADP to take backups using ODF Nooba Storage class.

## MariaDB Application setup 
Find the turorial here to setup full stack application 
(https://developers.redhat.com/learning/learn:openshift:learn-kubernetes-using-developer-sandbox/resource/resources:set-your-activity-environment)
Git repos for the source code
https://github.com/redhat-developer-demos/quotesweb.git
https://github.com/redhat-developer-demos/quotemysql.git
https://github.com/redhat-developer-demos/qotd-python.git

## Deploy OADP Yamls

