# Cluster Auth

## What is cluster auth?

Cluster auth refers to both authentication and authorization. This role can be used to configure integration with an Active Directory server for authentication to the OpenShift cluster, and synchronize Active Directory groups into OpenShift for the purposes of authorization.

## Role Variables

The following variables need to be defined:

`k8s_auth_username`: The username used for authenticating to the cluster

`k8s_auth_password`: The password used for authenticating to the cluster

`k8s_auth_host`: The API URL of the cluster

`validate_certs`: Set to `yes` or `no` depending on whether OpenShift API certificates are recognized by the ansible client

## Requirements

The kubernetes, openshift, and requests-oauthlib packages need to be installed before using this role.
```
pip3 install --user kubernetes openshift requests-oauthlib
```

## Example Playbook

Set up cluster auth:
```
    - hosts: playbook-runner
      tasks:
        - include_role:
            name: cluster-auth
```            
Remove cluster auth:
```
    - hosts: playbook-runner
      tasks:
        - include_role:
            name: cluster-auth
            tasks_from: uninstall.yml
```

