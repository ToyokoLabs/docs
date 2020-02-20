How to use gsutil to manage files
=================================


To copy, move or delete files from your machine to a Google Storage, you can use the Google GUI (aka <a href="https://console.cloud.google.com/" target="_blank">Google Cloud Console</a>) or the **gsutil** command. This tutorial explains the installation and use of gsutil to handle files in the command line.

Before installing **gsutil**, let's create a bucket using the Google Cloud Console.


Go to storage
-------------

In the <a href="https://console.cloud.google.com/" target="_blank">Google Cloud Console</a>, go to Storage and then Browse:


![Image of go to storage](imgs/Screen%20Shot%202020-02-04%20at%206.10.46%20PM.png?raw=true)


Create a bucket
---------------

Press CREATE BUCKET button in the console:

![Image of create bucket](imgs/Screen%20Shot%202020-02-04%20at%205.58.15%20PM.png?raw=true)


Next step is to name the bucket. Since the name must be unique (try joining multiple words and the name of your institute for example), you can also use a domain name if this belongs to you or you are authorized to use it, for example myuniquename.toyoko.io, change toyoko.io for your domain, then press CONTINUE.

**Note**: If you want to use a domain name and you are not authorized to do so, go to https://cloud.google.com/storage/docs/domain-name-verification for more information on how to get the authorization.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%205.58.37%20PM.png?raw=true)

Next step is to select the region. Unless you have a specific needs, choose *Region* in Location Type and *us-west-1 (Oregon)* in Location, then press CONTINUE.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.00.23%20PM.png?raw=true)


Select the storage class, select *Standard*, then press CONTINUE.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.00.36%20PM.png?raw=true)

In the *access control*, select *Fine-grained*, then press CONTINUE.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.00.50%20PM.png?raw=true)

In *Advanced Settings* leave the encryption as *Google-manage key* and press **CREATE**.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.16.08%20PM.png?raw=true)

After this, the bucket is created, so you can upload files to it.


Install gsutil (as part of Google Cloud SDK)
--------------------------------------------

Install following this guide according to your OS:

https://cloud.google.com/storage/docs/gsutil_install

Once the Google Cloud SDK is installed run the gcloud init command and follow the prompt (this may include opening a web page and log in with you Google account linked to your CGP project).

Check that **gsutil** is intalled by running (note you may have a different version):

```
$ gsutil --version
gsutil version: 4.47
```

Simple upload
-------------

To upload a file to a bucket in the command line use the gsutil command this way:

```
gsutil cp <YOUR_LOCAL_FILE> gs://<BUCKET_NAME>
```

So if your local file is called *readme.md* and your bucket is called *storage.balseiro.toyoko.io*, the command will look like: 


```
gsutil cp "readme.txt" gs://storage.balseiro.toyoko.io
```

Use of quotes are mandatory when the file name has white spaces.

This simple upload can work for large files since it has built-in resume for files larger than 8Mb, that means that if the upload is interrupted, the next try is intented it will continue the upload from the last chunck instead of starting over.

To upload large files (>250Mb) it is advisable to do it in multiple parts using the configuration shown in next section


Upload files in multiple parts
------------------------------

The first step is to verify that you gsutil installation supports this functionality. There is a module called *crcmod* that must be compiled. To verify this run this command:

```
gsutil version -l
```

and look for this line:

```
compiled crcmod: True
```

If it status is *True*, you can jump to step *Enable parallel upload* . If it is false, you need to compile it, this procedure is different for each platform, please read here: https://cloud.google.com/storage/docs/gsutil/addlhelp/CRC32CandInstallingcrcmod


Enable parallel upload:

Edit your .boto file (it should be in your home directory, in Linux is ~/.boto), and add these lines:

```
parallel_composite_upload_threshold = 250M
parallel_composite_upload_component_size = 80M
```

You can change the values (according to your internet speed), if you want to change them, use higher number than these.
Reset the terminal and the next gsutil cp command you will run, will run in parallel if the file is larger than the value in *parallel_composite_upload_threshold* variable.


NOTE
====

If you have a 403 error when uploading a file, check that the folder name exists in Google Storage and that you are authorized, if in doubt, run this:

```
gcloud auth login
```

Copy the link in a browser, authenticate and copy the token in the terminal.



Resources
---------

https://cloud.google.com/storage/docs/gsutil_install

https://cloud.google.com/storage/docs/quickstart-gsutil?hl=en_US

https://cloud.google.com/storage/docs/working-with-big-data

https://www.cloudbooklet.com/gsutil-cp-copy-and-move-files-on-google-cloud/
