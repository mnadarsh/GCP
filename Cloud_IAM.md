# Overview

Google Cloud's Identity and Access Management (IAM) service lets you create and manage permissions for GCP resources. Cloud IAM unifies access control for GCP services into a single system and provides a consistent set of operations. In this hands-on lab you learn how to assign a role to a second user and remove assigned roles associated with Cloud IAM. More specifically, you sign in with 2 different sets of credentials to experience how granting and revoking permissions works from GCP Project Owner and Viewer roles.


**Setup for two users**

As mentioned earlier, this lab provides two sets of credentials to illustrate IAM policies and what permissions are available for specific roles.

In the panel on the left-hand side of your lab, you see a list of credentials that resembles the following:

**Sign in to GCP Console as the first user**

Click on the Open Google Console button. This opens a new browser tab. If you are asked to Choose an account, click Use another account.

The GCP sign in page opens. A Sign in page opens—copy and paste the Username 1 credential that resembles googlexxxxxx_student@qwiklabs.net into the "Email or phone" field.

Copy the password from the "Connection Details" panel and paste into the Google Sign in password field.

Click Next and then Accept the terms of service. The Google Cloud Platform Console opens. 

Agree to the terms of service and check No for email updates:

**Sign in to GCP Console as the second user**

Click on the Open Google Console button again. A new browser tab opens, if you are asked to Choose an account, click Use another account.

The GCP sign in page opens. Copy and paste the Username 2 credential that resembles googlexxxxxx_student@qwiklabs.net into the Email or phone field.

Copy the password from the Connection Details panel and paste into the Google Sign in password field.

Click Next and then Accept the terms of service. The Google Cloud Platform Console opens. 

Agree to the terms of service and check No for email updates:


# The IAM console and project level roles

Return to the Username 1 GCP Console page.

Select Navigation menu > IAM & admin > IAM. You are now in the "IAM & admin" console.

Click +ADD button near the top of the page and explore the project roles associated with Projects by clicking on the "Select a role" dropdown menu:

*You should see Browser, Editor, Owner, and Viewer roles. These four are known as primitive roles in GCP. Primitive roles set project-level permissions and unless otherwise specified, they control access and management to all GCP services.*


**roles/viewer**
  Permissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data.
  
**roles/editor** 
  All viewer permissions, plus permissions for actions that modify state, such as changing existing resources.

**roles/owner**
  All editor permissions and permissions for the following actions:

  *. Manage roles and permissions for a project and all resources within the project.*
  *. Set up billing for a project.*
  
 **roles/browser (beta)**
  Read access to browse the hierarchy for a project, including the folder, organization, and Cloud IAM policy. 
  This role doesn't include  permission to view resources in the project.
