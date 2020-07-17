# Google Cloud Pub/Sub

## Overview
Google Cloud Pub/Sub is a messaging service for exchanging event data among applications and services. A producer of data publishes messages to a Cloud Pub/Sub topic. A consumer creates a subscription to that topic. Subscribers either pull messages from a subscription or are configured as webhooks for push subscriptions. Every subscriber must acknowledge each message within a configurable window of time.

  **You can list the active account name with this command**
  gcloud auth list
  
  **You can list the project ID with this command:**
  gcloud config list project
  
## Setting up Pub/Sub

  You can use the Google Cloud Shell console to perform operations in Google Cloud Pub/Sub.

  To use a Pub/Sub, you create a topic to hold data and a subscription to access data .published to the topic.
  
  1. Click Navigation menu > Pub/Sub > Topics.
  2. Click Create a topic.
  3. The topic must have a unique name. For this lab, name your topic MyTopic. In the Create a topic dialog:
    Name your topic ***MyTopic***.
    Leave Encryption at the default value.
    Click ***CREATE TOPIC***.
    
 ## Add a subscription
 
    Now you'll make a subscription to access the topic.

   1. Click Topics in the left panel to return to the Topics dialog. For the topic you just made click the three dot icon > Create subscription.
   2. In the **Add subscription** to topic dialog:
          Type a name for the subscription, such as ***MySub***
          Set the Delivery Type to ***Pull***.
          Leave all other options at the default values.
          Click ***Create***.
  
  ## Publish a message to the topic
  
   1. At the top of the ***Topics*** details dialog, click **PUBLISH MESSAGE**. You may have to widen the browser window to see the **PUBLISH MESSAGE** option.
   2. Enter `Hello World` in the **Message** field and click **Publish.**
   
  
  ## View the message
  
  To view the message you'll use the subscription (MySub) to pull the message (Hello World) from the topic (MyTopic).
    
   **Enter the following command in command line.**
   
      gcloud pubsub subscriptions pull --auto-ack MySub
  
  
