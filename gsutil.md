How to use gsutil to manage files
=================================


To copy, move or delete files from your machine to a Google Storage, you can use the Google GUI (aka [Google Cloud Console](https://console.cloud.google.com/)) or the **gsutil** command. This tutorial explains the installation and use of gsutil to handle files in the command line.

Before installing **gsutil**, let's create a bucket using the Google Cloud Console.


Go to storage
-------------

In the Google Cloud Console, go to Storage and then Browse:


![Image of go to storage](imgs/Screen%20Shot%202020-02-04%20at%206.10.46%20PM.png?raw=true)


Create a bucket
---------------

Press CREATE BUCKET button in the console:

![Image of create bucket](imgs/Screen%20Shot%202020-02-04%20at%205.58.15%20PM.png?raw=true)


Next step is to name the bucket. Since the name must be unique, a good idea is to use a domain name, for example myuniquename.toyoko.io, change toyoko.io for your domain, then press CONTINUE.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%205.58.37%20PM.png?raw=true)

Next step is to select the region. Unless you have a specific needs, choose *Region* in Location Type and *us-west-1 (Oregon)* in Location.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.00.23%20PM.png?raw=true)


Select the storage class, select *Standard*.

![Image of name bucket](imgs/Screen%20Shot%202020-02-04%20at%206.00.36%20PM.png?raw=true)

In the *access control*, select *Fine-grained*.

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

```
gsutil version -l
```


Resources
---------

https://cloud.google.com/storage/docs/gsutil_install

https://cloud.google.com/storage/docs/quickstart-gsutil?hl=en_US

https://cloud.google.com/storage/docs/working-with-big-data
