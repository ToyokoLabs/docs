
How to start a VM and login
===========================

Start the VM
------------

Go to the Console, Compute Engine, VM Instance. You should see the list of available VMs. Select the VM you want to start (1 in the screenshot) and then press the start button (2 in the screenshot)

![vm in the compute console](imgs/fig1.png?raw=true)

The start up process may take a time (up to 5 minutes), after this, you should see a green marker next to the VM name.

![VM working](imgs/fig2.png?raw=true)


Login from the web console
--------------------------

Click on the SSH button in the line of the VM you want to log in:

![ssh button](imgs/fig3.png?raw=true)

This will start a popup windows that will work as a terminal. Note that this windows also has the capability to upload/download files to your VM. This is in the menu associated with the gear in the top right part of the windows:

![web terminal with upload download menu](imgs/Screen%20Shot%202020-02-19%20at%203.38.05%20PM.png?raw=true)


Login from the cloud shell
--------------------------

In the cloud shell, run the login command.

The cloud shell:

![the cloud shell](imgs/fig4.png?raw=true)


Login command
-------------

Run the following command in the cloud shell:

```
gcloud compute ssh [VM_ANAME] --zone=[ZONE] --ssh-flag=-v 
```

For example:
```
gcloud compute ssh xxxtesla100 --zone=us-west2-a --ssh-flag=-v 
```


Permissions
-----------

In case of 403 error, check that the user has a role with at least the following permissions:

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

[See here](https://cloud.google.com/compute/docs/instances/managing-instance-access) for more information on how to do it.



More information
----------------

https://cloud.google.com/compute/docs/instances/connecting-to-instance

https://cloud.google.com/compute/docs/instances/managing-instance-access

