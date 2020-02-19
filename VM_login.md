

How to start a VM and login
===========================

Start the VM
------------

Go to the Console, Compute Engine, VM Instance. You should see the list of available VMs.

[INSERT IMAGE]



Permissions
-----------

Check that the user has a role with at least the following permissions:

compute.instances.osLogin
compute.instances.setMetadata
compute.projects.setCommonInstanceMetadata
iam.serviceAccounts.actAs

The user shouls also be part of the project as an "external user", in order to do that, the Admin should run this command:

```
gcloud organizations add-iam-policy-binding [PROJECTID] --member='user:[email]' --role='roles/compute.osLoginExternalUser'
```

For example:

```
gcloud organizations add-iam-policy-binding 333411111111 --member='user:user@example.com' --role='roles/compute.osLoginExternalUser'
````

Last thing to check, the instance (or the project) should have the **enable-oslogin** metadata set to **TRUE**.

[Se here](https://cloud.google.com/compute/docs/instances/managing-instance-access) for more information on how to do it.


Login from the web console
--------------------------

Click on the SSH button in the line of the VM you want to log in:

[INSERT IMAGE]

Login from the cloud shell
--------------------------

In the cloud shell, run the login command.

The cloud shell:

[INSER IMAGE]


Login command
-------------

```
gcloud compute ssh [VM_ANAME] --zone=[ZONE] --ssh-flag=-v 
```

For example:
```
gcloud compute ssh xxxtesla100 --zone=us-west2-a --ssh-flag=-v 
```


More information
----------------

https://cloud.google.com/compute/docs/instances/connecting-to-instance

https://cloud.google.com/compute/docs/instances/managing-instance-access

