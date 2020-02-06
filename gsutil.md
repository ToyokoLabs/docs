How to use gsutil to manage files
=================================


To copy, move or delete files from your machine to a Google Storage, you can use the Google GUI or the gsutil command. This tutorial explains the installation and use of gsutil to handle files in the command line.

Install gsutil (as part of Google Cloud SDK)
--------------------------------------------

Install following this guide according to your OS:

https://cloud.google.com/storage/docs/gsutil_install

Once the Google Cloud SDK is installed run the gcloud init command and follow the prompt (this may include opening a web page and log in with you Google account linked to your CGP project).


In the Google Cloud Console, go to Storage and then Browse:

INSERT FIGURE


![Image of create bucket](imgs/Screen%20Shot%202020-02-04%20at%206.10.46%20PM.png?raw=true)


Create a bucket
---------------

Press CREATE BUCKET button in the console:

![Image of create bucket](imgs/Screen%20Shot%202020-02-04%20at%205.58.15%20PM.png?raw=true)





Simple upload:

gsutil cp "/Volumes/Samsung USB/music/musicForProgramming 1-52/music_for_programming_47-abe_mangger.mp3" gs://storagetest.balseiro.toyoko.io





Resources
---------

https://cloud.google.com/storage/docs/gsutil_install

https://cloud.google.com/storage/docs/quickstart-gsutil?hl=en_US

https://cloud.google.com/storage/docs/working-with-big-data
