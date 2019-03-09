# ansible-role-eks
Ansible role for managing AWS EKS clusters (controlplane + nodes)

## Requirements
An AWS account and credentials with permissions to manipulate VPC, EC2, EKS, IAM.

System packages:
* botocore (botocore must be 1.10.32 or above)
* kubectl (kubectl must be 1.10.0+ to work with aws-iam-authenticator)
* Python client for OpenShift http://openshift.redhat.com/
* aws-iam-authenticator (https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html#eks-prereqs)

## Dependencies
None.

## Example Playbooks
EKS.yml
```
---
- hosts: localhost
  gather_facts: false
  vars:
    REGION: eu-west-1
    aws_access_key: "{{ AWS_ACCESS_KEY }}"
    aws_secret_key: "{{ AWS_SECRET_KEY }}"
  roles:
    - role: ansible-role-eks
```
**Create or modify cluster**  
ansible-playbook EKS.yml -e eks_action=setup

**Delete cluster (controlplane + nodes)**  
ansible-playbook EKS.yml -e eks_action=teardown

### Notes
Based in the work of https://github.com/willthames/ansiblefest2018/tree/master/ansible/roles/eks
