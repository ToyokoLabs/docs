
How to mount a Google Storage bucket into a local directory
===========================================================

For Linux
---------

This is a 2 step process. Install FUSE and mount the bucket as a directory using FUSE.

Installing FUSE
---------------

Copy and run the following commands, this will add a new repo to install FUSE:

```
export GCSFUSE_REPO=gcsfuse-`lsb_release -c -s`
echo "deb http://packages.cloud.google.com/apt $GCSFUSE_REPO main" | sudo tee /etc/apt/sources.list.d/gcsfuse.list
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```

Update your repository and install FUSE:

```
sudo apt-get update
sudo apt-get install gcsfuse
```

Mounting the bucket
-------------------

Create a directory, that will be used to mount your bucket:

```
mkdir /mnt/disks/bucket
```

Now you can use the *gcsfuse* util to mount the bucket. If your bucket is called *mybucket* and your mount point is */mnt/disks/bucket*

```
gcsfuse mybucket /mnt/disks/bucket
```

Now you can use standard Unix command to interact with files in the bucket.


More information
----------------

The instructions in this document were tested with Ubuntu 18.04.3 LTS and authenticated with *gcloud auth login*. Check the following link for different Operating Systems and authentication methods.

https://github.com/GoogleCloudPlatform/gcsfuse/blob/master/docs/installing.md




