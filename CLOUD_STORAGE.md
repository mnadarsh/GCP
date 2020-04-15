Google Cloud Storage allows world-wide storage and retrieval of any amount of data at any time. You can use Google Cloud Storage for a range of scenarios including serving website content, storing data for archival and disaster recovery, or distributing large data objects to users via direct download.

# Steps to work on 

Activate Google Cloud Shell
Google Cloud Shell is a virtual machine that is loaded with development tools. It offers a persistent 5GB home directory and runs on the Google Cloud. Google Cloud Shell provides command-line access to your GCP resources.

step 1 

In GCP console, on the top right toolbar, click the Open Cloud Shell button.

gcloud auth list

## gcloud config list project


**Create a bucket**
Run the gsutil mb command and replace with a unique name to create a bucket:

gsutil mb gs://YOUR-BUCKET-NAME/

Bucket naming rules:

Do not include sensitive information in the bucket name, because the bucket namespace is global and publicly visible.
Bucket names must contain only lowercase letters, numbers, dashes (-), underscores (_), and dots (.). Names containing dots require verification.
Bucket names must start and end with a number or letter.
Bucket names must contain 3 to 63 characters. Names containing dots can contain up to 222 characters, but each dot-separated component can be no longer than 63 characters.
Bucket names cannot be represented as an IP address in dotted-decimal notation (for example, 192.168.5.4).
Bucket names cannot begin with the "goog" prefix.
Bucket names cannot contain "google" or close misspellings of "google".
Also, for DNS compliance and future compatibility, you should not use underscores (_) or have a period adjacent to another period or dash. For example, ".." or "-." or ".-" are not valid in DNS names.

If successful, the command returns:

Creating gs://YOUR-BUCKET-NAME/...


# Upload an object into your bucket

    **First, download this image to a temporary instance (ada.jpg) in Cloud Shell:**
      *code below*
      
        wget --output-document ada.jpg https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg
        
    **Use the gsutil cp command to upload the image from the location where you saved it to the bucket you created:**
    
        gsutil cp ada.jpg gs://YOUR-BUCKET-NAME
        
     **Now remove the downloaded image:**
        
        rm ada.jpg
        
    
# Download an object from your bucket

    **Use the gsutil cp command to download the image you stored in your bucket to Cloud Shell:**
    
          gsutil cp -r gs://YOUR-BUCKET-NAME/ada.jpg .
          
          

