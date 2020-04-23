# Overview

In this lab you will use gsutil to create a bucket and perform operations on objects. gsutil is a Python application that lets you access Cloud Storage from the command line. The gsutil tool has commands such as mb and cp to perform operations. Each command has a set of options that are used to customize settings further.


## What you'll learn to do

Create a bucket

Copy files from a local folder to a bucket

Synchronize the contents of the local folder with the contents of the bucket

Change access control permissions on objects

Delete a bucket.


   **In Cloud Shell session execute the following command to download sample data for this lab from a git repository:**

    git clone https://github.com/GoogleCloudPlatform/training-data-analyst
    
   *Change to the blogs directory:*
   
    cd training-data-analyst/blogs
    
 # Working with buckets and objects
 
   *First, set some environment variables:*
   
      PROJECT_ID=`gcloud config get-value project`
      BUCKET=${PROJECT_ID}-bucket
      
 **Create a bucket**
 
   *Create a bucket and multi-regional storage class:*
   
      gsutil mb -c multi_regional gs://${BUCKET}
      
 **Upload objects to your bucket**
 
  *Run the following to copy the endpointslambda object to your bucket:*
      
      gsutil -m cp -r endpointslambda gs://${BUCKET}
      
   *If you have a large number of files to transfer, you might want to use the -m option, to perform
      a parallel (multi-threaded/multi-processing) copy for faster performance. The -r option allows gsutil
      to recurse through directories.*
      
  **List objects**

  *To list objects in your bucket, execute the following command:*
  
      gsutil ls gs://${BUCKET}/*
      
   **Sync changes with bucket**

  *Use the following commands to rename and delete some files:*
  
    mv endpointslambda/Apache2_0License.txt endpointslambda/old.txt
    
    rm endpointslambda/aeflex-endpoints/app.yaml
    
  **Now synchronize the local changes with the bucket:**
    
    gsutil -m rsync -d -r endpointslambda gs://${BUCKET}/endpointslambda
    
   *In this command, the -d option deletes files from the target if they're missing in the 
      source (in this case, it deletes app.yaml from the bucket). 
      The -r option runs the command recursively on directories.*
      
   **To verify that the bucket is now in sync with your local changes, list the files in the bucket again:**
   
      gsutil ls gs://${BUCKET}/*
      
  **Make objects public**

   *To allow public access to all files under the endpointslambda folder in your bucket, execute the following command:*
   
      gsutil -m acl set -R -a public-read gs://${BUCKET}
      
   *To confirm files are viewable by the public, open the following link in a new incognito or private browser window,
   replacing <your-bucket-name> with the full name of your bucket, not the environment variable:*
  
  
      
