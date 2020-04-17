# Overview

Cloud Monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. Cloud monitoring collects metrics, events, and metadata from Google Cloud, Amazon Web Services, hosted uptime probes, application instrumentation, and a variety of common application components including Cassandra, Nginx, Apache Web Server, Elasticsearch, and many others. Cloud monitoring ingests that data and generates insights via dashboards, charts, and alerts. Cloud monitoring alerting helps you collaborate by integrating with Slack, PagerDuty, HipChat, Campfire, and more.

This hands-on lab shows you how to monitor a Google Compute Engine virtual machine (VM) instance with Cloud monitoring. You'll also install monitoring and logging agents for your VM which collects more information from your instance, which could include metrics and logs from 3rd party apps.

# Create a Compute Engine instance

1. In the Cloud Console dashboard, go to Navigation menu > Compute Engine > VM instances, then click Create.
2. Fill in the fields as follows, leaving all other fields at the default value:

      Name: lamp-1-vm

      Region: us-central1 (Iowa) or asia-south1 (Mumbai)

      Zone: us-central1-a or asia south1-a

      Machine type: n1-standard-2

      Firewall: Select Allow HTTP traffic
 3. Click Create.
  
      Wait a couple of minutes, you'll see a green check when the instance has launched.
      
  # Add Apache2 HTTP Server to your instance
  
     1. In the Console, click SSH to open a terminal to your instance.
     
     2. Run the following commands in the SSH window to set up Apache2 HTTP Server:
     
                sudo apt-get update
                
                sudo apt-get install apache2 php7.0
                
                sudo service apache2 restart
     
     3. Return to the console, on the VM instances page. Click the External IP for lamp-1-vm instance to see the 
        Apache2 default page for this instance.
        
   # Create a Monitoring workspace
   
      1. In the Google Cloud Platform Console, click on Navigation menu > Monitoring.
      
      2. Wait for your workspace to be provisioned.

         When the Monitoring dashboard opens, your workspace is ready.
         
      *Agents collect data and then send or stream info to Cloud Monitoring in the Console.*
      
      The Cloud Monitoring agent is a collectd-based daemon that gathers system and application metrics from virtual machine
      instances and sends them to Monitoring. By default, the Monitoring agent collects disk, CPU, network, and process
      metrics. Configuring the Monitoring agent allows third-party applications to get the full list of agent metrics. Learn more.
      
      The Cloud Logging agent streams logs from your VM instances and from selected third-party software packages to Cloud Logging.
      It is a best practice to run the Cloud Logging agent on all your VM instances. Learn more.
      
   # To install the agents on the VM:
   
      1. In the Monitoring Overview window, click INSTALL AGENTS in the Install agents tile. The Monitoring Agent window opens 
      and provides install scripts for the Monitoring and Logging agents.
      
      2. Run the Monitoring agent install script command in the SSH terminal of your VM instance to install the Cloud Monitoring agent.
      
      3. Run the Logging agent install script command in the SSH terminal of your VM instance to install the Cloud Logging agent.
      
   # Create an uptime check
   
      Uptime checks verify that a resource is always accessible. For practice, create an uptime check to verify your VM is up.
      
      1. In the Console, in the left menu, click Uptime checks, and then click Create Uptime Check.
      
      2. Set the following fields:
      
              Title: Lamp Uptime Check

              Check type: HTTP

              Resource Type: Instance

              Applies to: Single, lamp-1-vm

              Path: leave at default

              Check every: 1 min
      
      3. Click Test to verify that your uptime check can connect to the resource.
      
      4. When you see a green check mark everything can connect. Click Save
      
      5. Click No, thanks to create an alerting policy for this check.
      
   # Create an alerting policy
   
      Use Cloud monitoring to create one or more alerting policies.
      
      1. In the left menu, click Alerting, and then click Create Policy.
      
      2. Name the alerting policy "Inbound Traffic Alert".

          You'll next configure Conditions, Notifications, and Documentation.
          
          1. Conditions: click Add Condition.
              Set the following in the panel that opens, leave all other fields at the default value.
              
              Target: Start typing "GCE" in the resource type and metric field, and then select:
              
              . Resource Type: GCE VM Instance (gce_instance)
              
              . Metric: Type "network", and then select Network traffic (gce_instance+1.). Be sure to choose the 
                Network traffic resource with agent.googleapis.com/interface/traffic:
                
                Configuration

                    Condition: is above

                    Threshold: 500

                     For: 1 minute
                     
                 Click Add.

          2. Notifications: Click Add Notification Channel.
                  
                  Select Email Address, then enter your personal email address in the Email field.
                  
          3. Documentation: Add a message in documentation, which will be included in the emailed alert.
          
          Click Save at the bottom of the Create new alerting policy dialog.

          You've created an alert! While you wait for the system to trigger an alert, 
          create a dashboard and chart, and then check out Cloud logging.
          
          
  # Create a dashboard and chart
   
      You can display the metrics collected by Cloud Monitoring in your own charts and dashboards.
      In this section you create the charts for the lab metrics and a custom dashboard.
      
      1. In the left menu select Dashboards, and then Create Dashboard.
      
      2. Name the dashboard "Cloud monitoring LAMP Qwik Start Dashboard", and then click Confirm.
      
      Add the first chart
      
            1. Click Add Chart in the top right of the screen.
      
            2. Name the chart "CPU Load".
      
            3. Click into the Find resource type and metric field and start typing "CPU load", then select CPU Load (1m).
            
            4. Set the resource type to "GCE VM Instance".
            
      Add the second chart
      

