

How to start a VM and login
===========================

Start the VM
------------

Go to the Console, Compute Engine, VM Instance. You should see the list of available VMs.

[INSERT IMAGE]




Permissions
-----------




```
gcloud organizations add-iam-policy-binding [PROJECTID] --member='user:[email]' --role='roles/compute.osLoginExternalUser'
```

For example:

```
gcloud organizations add-iam-policy-binding 333411111111 --member='user:user@example.com' --role='roles/compute.osLoginExternalUser'
````




Login from the web console
--------------------------



Login from the cloud shell
--------------------------

Login command
-------------

```
gcloud compute ssh [VM_ANAME] --zone=[ZONE] --ssh-flag=-v 
```

For example:
```
gcloud compute ssh xxxtesla100 --zone=us-west2-a --ssh-flag=-v 
```
