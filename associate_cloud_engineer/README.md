# associate-cloud-engineer-sample-question

1. Every employee of your company has a Google account. Your operational team needs to manage a large number of instances on Compute Engine. Each member of this team needs only administrative access to the servers. Your security team wants to ensure that the deployment of credentials is operationally efficient and must be able to determine who accessed a given instance. What should you do?
	- A. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key in the metadata of each instance.
	- B. Ask each member of the team to generate a new SSH key pair and to send you their public key. Use a configuration management tool to deploy those keys on each instance.
	- C. Ask each member of the team to generate a new SSH key pair and to add the public key to their Google account. Grant the compute.osAdminLogin role to the Google group corresponding to this team.
	- D. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key as a project-wide public SSH key in your Cloud Platform project and allow project-wide public SSH keys on each instance.
	
	- **C**. Each member should have their own SSH key for security reason. For accessing resource, you add user to group and grand permssion to the role
	
2. You need to create a custom VPC with a single subnet. The subnet's range must be as large as possible. Which range should you use?
	- A. 0.0.0.0/0
	- B. 10.0.0.0/8
	- C. 172.16.0.0/12
	- D. 192.168.0.0/16
	
	- **B**. The smaller number after / the more IP address it can provide in a single subnet. For custom subnet, the minimum size is /8. 
	
3. You want to select and configure a cost-effective solution for relational data on Google Cloud Platform. You are working with a small set of operational data in one geographic location. You need to support point-in-time recovery. What should you do?
	- A. Select Cloud SQL (MySQL). Verify that the enable binary logging option is selected.
	- B. Select Cloud SQL (MySQL). Select the create failover replicas option.
	- C. Select Cloud Spanner. Set up your instance with 2 nodes.
	- D. Select Cloud Spanner. Set up your instance as multi-regional.
	
	- **A**. Small set of data in one geographic location, the best option would be Cloud SQL. Point-in-time recovery is a way to roll back data in a specific time in the past. Point-in-time recovery use binary logs, you need to enable binary logging in order to perform this action 
	
4. You want to configure autohealing for network load balancing for a group of Compute Engine instances that run in multiple zones, using the fewest possible steps.
You need to configure re-creation of VMs if they are unresponsive after 3 attempts of 10 seconds each. What should you do?

	- A. Create an HTTP load balancer with a backend configuration that references an existing instance group. Set the health check to healthy (HTTP)
	- B. Create an HTTP load balancer with a backend configuration that references an existing instance group. Define a balancing mode and set the maximum RPS to 10.
	- C. Create a managed instance group. Set the Autohealing health check to healthy (HTTP)
	- D. Create a managed instance group. Verify that the autoscaling setting is on.
	
	- **C**. Created managed instance group allows you to use autohealing to automatically recreate VMs that are unresponsive after 3 attempts for 10 sec. Other answer did not mentioned autohealing.
	
5. You are using multiple configurations for gcloud. You want to review the configured Kubernetes Engine cluster of an inactive configuration using the fewest possible steps. What should you do?
	- A. Use gcloud config configurations describe to review the output.
	- B. Use gcloud config configurations activate and gcloud config list to review the output.
	- C. Use kubectl config get-contexts to review the output.
	- D. Use kubectl config use-context and kubectl config view to review the output.
	
	- **D**. `kubectl config view` allows you to view Kubernetes Engine configuration. When you have multiple configuration, use `kubectl config use-context` to specify which context/clusters you want to views. `kubectl config get-contexts` do not output detail configuration
	
6. Your company uses Cloud Storage to store application backup files for disaster recovery purposes. You want to follow Google's recommended practices. Which storage option should you use?
	- A. Multi-Regional Storage
	- B. Regional Storage
	- C. Nearline Storage
	- D. Coldline Storage
	
	- **D**. The best options is Archive Storage as per documentation. https://cloud.google.com/storage/docs/storage-classes#archive Consider the above 4 options, the next best answer is Coldline storage that is low in writing cost
	
7. Several employees at your company have been creating projects with Cloud Platform and paying for it with their personal credit cards, which the company reimburses. The company wants to centralize all these projects under a single, new billing account. What should you do?
	- A. Contact cloud-billing@google.com with your bank account details and request a corporate billing account for your company.
	- B. Create a ticket with Google Support and wait for their call to share your credit card details over the phone.
	- C. In the Google Platform Console, go to the Resource Manage and move all projects to the root Organizarion.
	- D. In the Google Cloud Platform Console, create a new billing account and set up a payment method.
	
	- **D** You want to create a new billing account, setup payment. and then move the project under the billing account
	
8. You have an application that looks for its licensing server on the IP 10.0.3.21. You need to deploy the licensing server on Compute Engine. You do not want to change the configuration of the application and want the application to be able to reach the licensing server. What should you do?
	- A. Reserve the IP 10.0.3.21 as a static internal IP address using gcloud and assign it to the licensing server.
	- B. Reserve the IP 10.0.3.21 as a static public IP address using gcloud and assign it to the licensing server.
	- C. Use the IP 10.0.3.21 as a custom ephemeral IP address and assign it to the licensing server.
	- D. Start the licensing server with an automatic ephemeral IP address, and then promote it to a static internal IP address.
	
	- **A**. To make sure IP 10.0.3.21 do not change, you want to reserve this IP as a static IP. As per https://cloud.google.com/vpc/docs/subnets#valid-ranges, IP start with **10, 172.16, 192.168** are private / internal IP address
	
9. You are deploying an application to App Engine. You want the number of instances to scale based on request rate. You need at least 3 unoccupied instances at all times. Which scaling type should you use?
	- A. Manual Scaling with 3 instances.
	- B. Basic Scaling with min_instances set to 3.
	- C. Basic Scaling with max_instances set to 3.
	- D. Automatic Scaling with min_idle_instances set to 3.
	
	- **D**. App Engine offer Automatic, Basic and Manual scalling. Automatically scalling allows you to scale based on request rate and other metrics such as CPU and memory utilization. Can set `min_idle_instances` to ensure always a number of unoccupied instance available

10. You have a development project with appropriate IAM roles defined. You are creating a production project and want to have the same IAM roles on the new project, using the fewest possible steps. What should you do?
	- A. Use gcloud iam roles copy and specify the production project as the destination project.
	- B. Use gcloud iam roles copy and specify your organization as the destination organization.
	- C. In the Google Cloud Platform Console, use the 'create role from role' functionality.
	- D. In the Google Cloud Platform Console, use the 'create role' functionality and select all applicable permissions.
	
	- **A**. Can copy cloud IAM role to organizations or to projects. https://cloud.google.com/sdk/gcloud/reference/iam/roles/copy In this scenarios, we want to copy cloud iam role to a specific project, not to all projects inside of organization .So A is correct, `gcloud iam roles copy --source="roles/spanner.databaseAdmin" --destination=CustomSpannerDbAdmin --dest-project=PROJECT_ID`

11. You need a dynamic way of provisioning VMs on Compute Engine. The exact specifications will be in a dedicated configuration file. You want to follow Google's recommended practices. Which method should you use?
	- A. Deployment Manager
	- B. Cloud Composer
	- C. Managed Instance Group
	- D. Unmanaged Instance Group
	
	- **A** Deployment Manager is a configuration management tool that allows you to define and deploy resources. You create a configuration that can be used to create deployments, which is YAML syntax. Instance group let you operates apps on multiple identical VMs as single entity. For example, auto scalling and load balancing. In general, DM do creation and provisiong. IG do operating
	
12. You have a Dockerfile that you need to deploy on Kubernetes Engine. What should you do?
	- A. Use kubectl app deploy <dockerfilename>.
	- B. Use gcloud app deploy <dockerfilename>.
	- C. Create a docker image from the Dockerfile and upload it to Container Registry. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.
	- D. Create a docker image from the Dockerfile and upload it to Cloud Storage. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.
	
	- **C**. To deploy to Kubernetes, first create an image and push to container registry. Then create a deployment YAML file to specify the image to use and other options. Finally, use `kubectl` command to create deployment based on YAML filt to Kubernetes
	
13. Your development team needs a new Jenkins server for their project. You need to deploy the server using the fewest steps possible. What should you do?
	- A. Download and deploy the Jenkins Java WAR to App Engine Standard.
	- B. Create a new Compute Engine instance and install Jenkins through the command line interface.
	- C. Create a Kubernetes cluster on Compute Engine and create a deployment with the Jenkins Docker image.
	- D. Use GCP Marketplace to launch the Jenkins solution.
	
	- **D**. Since there is no need for any customization, using GCP Marketplace is a great option with minimum steps. All A, B, C involve certain configuation works and are suitable for customized work
	
14. You need to update a deployment in Deployment Manager without any resource downtime in the deployment. Which command should you use?
	- A. gcloud deployment-manager deployments create --config <deployment-config-path>
	- B. gcloud deployment-manager deployments update --config <deployment-config-path>
	- C. gcloud deployment-manager resources create --config <deployment-config-path>
	- D. gcloud deployment-manager resources update --config <deployment-config-path>
	
	- **B**. The deployment manager command set looks like `gcloud deployment-manager deployments xxx`. resources is not a valid keyword in Deployment Manager service. For update, we use `update` action
	
15. You need to run an important query in BigQuery but expect it to return a lot of records. You want to find out how much it will cost to run the query. You are using on-demand pricing. What should you do?
	- A. Arrange to switch to Flat-Rate pricing for this query, then move back to on-demand.
	- B. Use the command line to run a dry run query to estimate the number of bytes read. Then convert that bytes estimate to dollars using the Pricing Calculator.
	- C. Use the command line to run a dry run query to estimate the number of bytes returned. Then convert that bytes estimate to dollars using the Pricing Calculator.
	- D. Run a select count (*) to get an idea of how many records your query will look through. Then convert that number of rows to dollars using the Pricing Calculator.
	
	- **B**. On-demand pricing charge by **the number of bytes processed**, you can use `dry run` to estimate this. https://cloud.google.com/bigquery/docs/estimate-costs
	
16. You have a single binary application that you want to run on Google Cloud Platform. You decided to automatically scale the application based on underlying infrastructure CPU usage. Your organizational policies require you to use virtual machines directly. You need to ensure that the application scaling is operationally efficient and completed as quickly as possible. What should you do?
	- A. Create a Google Kubernetes Engine cluster, and use horizontal pod autoscaling to scale the application.
	- B. Create an instance template, and use the template in a managed instance group with autoscaling configured.
	- C. Create an instance template, and use the template in a managed instance group that scales up and down based on the time of day.
	- D. Use a set of third-party tools to build automation around scaling the application up and down, based on Stackdriver CPU usage monitoring.
	
	- **B**. Require to use VM directly so has to choose Compute Engine. Also to scale efficiently and quick based on CPU usage fall under autoscalling based on CPU utilization metric

17. You are analyzing Google Cloud Platform service costs from three separate projects. You want to use this information to create service cost estimates by service type, daily and monthly, for the next six months using standard query syntax. What should you do?
	- A. Export your bill to a Cloud Storage bucket, and then import into Cloud Bigtable for analysis.
	- B. Export your bill to a Cloud Storage bucket, and then import into Google Sheets for analysis.
	- C. Export your transactions to a local file, and perform analysis with a desktop tool.
	- D. Export your bill to a BigQuery dataset, and then write time window-based SQL queries for analysis.
	
	- **D**. To analyze data in GCP, there are two type of service. BigQuery and BigTable. Here it mentioned standard query syntax, which is SQL. So use BigQuery. In fact, it is recommended in cloud billing https://cloud.google.com/billing/docs/how-to/export-data-bigquery to export data to BigQuery
	
18. You need to set up a policy so that videos stored in a specific Cloud Storage Regional bucket are moved to Coldline after 90 days, and then deleted after one year from their creation. How should you set up the policy?
	- A. Use Cloud Storage Object Lifecycle Management using Age conditions with SetStorageClass and Delete actions. Set the SetStorageClass action to 90 days and the Delete action to 275 days
	- B. Use Cloud Storage Object Lifecycle Management using Age conditions with SetStorageClass and Delete actions. Set the SetStorageClass action to 90 days and the Delete action to 365 days.
	- C. Use gsutil rewrite and set the Delete action to 275 days (365-90).
	- D. Use gsutil rewrite and set the Delete action to 365 days.
	
	- **B** Use Cloud Storage Object Lifecycle Management using Age condition to change storage class. Trigger SetStorageAction to 90days to move from Standard to Coldline. And Set 365 days for Delete action. Because change storage class do not affect the age of object. It always calculated from creation time
	
19. You have a Linux VM that must connect to Cloud SQL. You created a service account with the appropriate access rights. You want to make sure that the VM uses this service account instead of the default Compute Engine service account. What should you do?
	- A. When creating the VM via the web console, specify the service account under the 'Identity and API Access' section.
	- B. Download a JSON Private Key for the service account. On the Project Metadata, add that JSON as the value for the key compute-engine-service- account.
	- C. Download a JSON Private Key for the service account. On the Custom Metadata of the VM, add that JSON as the value for the key compute-engine- service-account.
	- D. Download a JSON Private Key for the service account. After creating the VM, ssh into the VM and save the JSON under ~/.gcloud/compute-engine-service- account.json.
	
	- **A (Debating)**. I think A is correct. You can "run the VM as a different identity" by "change sthe service account and the access scope". By doing that you go to Web Console, create a Service Account and choose the service account under "Identify and API Access". https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#console and https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#changeserviceaccountandscopes
	
20. You created an instance of SQL Server 2017 on Compute Engine to test features in the new version. You want to connect to this instance using the fewest number of steps. What should you do?
	- A. Install a RDP client on your desktop. Verify that a firewall rule for port 3389 exists.
	- B. Install a RDP client in your desktop. Set a Windows username and password in the GCP Console. Use the credentials to log in to the instance.
	- C. Set a Windows password in the GCP Console. Verify that a firewall rule for port 22 exists. Click the RDP button in the GCP Console and supply the credentials to log in.
	- D. Set a Windows username and password in the GCP Console. Verify that a firewall rule for port 3389 exists. Click the RDP button in the GCP Console, and supply the credentials to log in.
	
	- **B (debating)**. SQL Server is running on Windows VM. So we are looking at some RDP (remote desktop protocal). Set the password and username, by default port 3389 firewall rule exist. Here, other people said they verify the RDP button on GCP Console take you to your local RDP Client. So B seems to be correct
	
21. You have one GCP account running in your default region and zone and another account running in a non-default region and zone. You want to start a new
Compute Engine instance in these two Google Cloud Platform accounts using the command line interface. What should you do?
	- A. Create two configurations using gcloud config configurations create [NAME]. Run gcloud config configurations activate [NAME] to switch between accounts when running the commands to start the Compute Engine instances.
	- B. Create two configurations using gcloud config configurations create [NAME]. Run gcloud configurations list to start the Compute Engine instances.
	- C. Activate two configurations using gcloud configurations activate [NAME]. Run gcloud config list to start the Compute Engine instances.
	- D. Activate two configurations using gcloud configurations activate [NAME]. Run gcloud configurations list to start the Compute Engine instances.
	
	- **A**, First, `gcloud config configurations` is the correct command set. Then, `list` verb does not start Compute Engine Instance. Finally, to start two VM, you first create two configuration. Then you activate them based on the account you want to activate

22. You significantly changed a complex Deployment Manager template and want to confirm that the dependencies of all defined resources are properly met before committing it to the project. You want the most rapid feedback on your changes. What should you do?
	- A. Use granular logging statements within a Deployment Manager template authored in Python.
	- B. Monitor activity of the Deployment Manager execution on the Stackdriver Logging page of the GCP Console.
	- C. Execute the Deployment Manager template against a separate project with the same configuration, and monitor for failures.
	- D. Execute the Deployment Manager template using the ג€"-preview option in the same project, and observe the state of interdependent resources.
	
	- **D** Deployment manager has Preivew functionaility that allows you to see updated deployment before commiting any change. Use Preview Configuration. https://cloud.google.com/deployment-manager/docs/deployments/updating-deployments#optional_preview_an_updated_configuration
	
23. You are building a pipeline to process time-series data. From the beginning it is data coming from IoT, then goes to standard HTTPs device. What would be the next steps after this? 
	- A. Cloud Pub/Sub, Cloud Dataflow, Cloud Datastore, BigQuery
	- B. Firebase Messages, Cloud Pub/Sub, Cloud Spanner, BigQuery
	- C. Cloud Pub/Sub, Cloud Storage, BigQuery, Cloud Bigtable
	- D. Cloud Pub/Sub, Cloud Dataflow, Cloud Bigtable, BigQuery
	
	- **D**. First, we want a real time messaging service for data. You can choose Cloud Pub/Sub or Firebase. Then we need a unified data streaming and data processing service. Cloud Dataflow is a great candidates. For storage, IoT in unstructured data, and only Cloud BigTable is able to handle time-series data. So D is correct
	
24. You have a project for your App Engine application that serves a development environment. The required testing has succeeded and you want to **create a new project** to serve as your production environment. What should you do?
	- A. Use gcloud to create the new project, and then deploy your application to the new project.
	- B. Use gcloud to create the new project and to copy the deployed application to the new project.
	- C. Create a Deployment Manager configuration file that copies the current App Engine deployment into a new project.
	- D. Deploy your application again using gcloud and specify the project parameter with the new project name to create the new project.
	
	- **A**, Need a new project, and deploy the App to that project. Deployment Manager has no ability to create new project. And you cannot copy a deployed application. Creating a project has to be an explicit step. So A is the only option
 
25. You need to configure IAM access audit logging in BigQuery for external auditors. You want to follow Google-recommended practices. What should you do?
	- A. Add the auditors group to the 'logging.viewer' and 'bigQuery.dataViewer' predefined IAM roles.
	- B. Add the auditors group to two new custom IAM roles.
	- C. Add the auditor user accounts to the 'logging.viewer' and 'bigQuery.dataViewer' predefined IAM roles.
	- D. Add the auditor user accounts to two new custom IAM roles.
	
	- **A**. First, you want to assign user to group, then group to roles. So C and D not correct. You want to use least priviledge concept, to give as minimal as permission, also use predefined role if possible. So compared A and B, A is enougth, B is not very specific. Also, for auditing, you gieve `bigQuery.dataViewer` for external auditor to see historical data. If they find something, you may grant `logging.viewer` role to see more logging info as needed. https://cloud.google.com/iam/docs/job-functions/auditing#scenario_external_auditors

26. You need to set up permissions for a set of Compute Engine instances to enable them to write data into a particular Cloud Storage bucket. You want to follow
Google-recommended practices. What should you do?
	- A. Create a service account with an access scope. Use the access scope 'https://www.googleapis.com/auth/devstorage.write_only'.
	- B. Create a service account with an access scope. Use the access scope 'https://www.googleapis.com/auth/cloud-platform'.
	- C. Create a service account and add it to the IAM role 'storage.objectCreator' for that bucket.
	- D. Create a service account and add it to the IAM role 'storage.objectAdmin' for that bucket.
	
	- **C**. You create a service account, grant it IAM role based on least priviledge concept. It says you want to write data to cloud storage, so `storage.objectCreator` is appropriate. Alternatively, you can use access scope which is a legacy method to access 'https://www.googleapis.com/auth/devstorage'. However, there is no write_only scope
	
27. You have sensitive data stored in three Cloud Storage buckets and have enabled data access logging. You want to verify activities for a particular user for these buckets, using the fewest possible steps. You need to verify the addition of metadata labels and which files have been viewed from those buckets. What should you do?
	- A. Using the GCP Console, filter the Activity log to view the information.
	- B. Using the GCP Console, filter the Stackdriver log to view the information.
	- C. View the bucket in the Storage section of the GCP Console.
	- D. Create a trace in Stackdriver to view the information.
	
	- **B** (Debating). B is more likely to be correct. We need to view not only data access / activity log. We need to view data accesss log plus who add the labels. SO use Stackdriver log to view completed information

28. You are the project owner of a GCP project and want to delegate control to colleagues to manage buckets and files in Cloud Storage. You want to follow Google- recommended practices. Which IAM roles should you grant your colleagues?
	- A. Project Editor
	- B. Storage Admin
	- C. Storage Object Admin
	- D. Storage Object Creator
	
	- **B**. Storage Admin give you full control to Gloud Storage Bucket and anything inside of buckets. Storage Object Admin only give you full controls to storage object, but not bucket. To "Manage", you need full control. https://cloud.google.com/storage/docs/access-control/iam-roles

29. You have an object in a Cloud Storage bucket that you want to share with an external company. The object contains sensitive data. You want access to the content to be removed after four hours. The external company does not have a Google account to which you can grant specific user-based access privileges. You want to use the most secure method that requires the fewest steps. What should you do?
	- A. Create a signed URL with a four-hour expiration and share the URL with the company.
	- B. Set object access to 'public' and use object lifecycle management to remove the object after four hours.
	- C. Configure the storage bucket as a static website and furnish the object's URL to the company. Delete the object from the storage bucket after four hours.
	- D. Create a new Cloud Storage bucket specifically for the external company to access. Copy the object to that bucket. Delete the bucket after four hours have passed.
	
	- **A**. Signed URL give time-limited access to a specific Cloud Storage resource. Mostly when your users do not have Google Account. Signed URL must specify a user or service account who has sufficient permission to make the request. See here https://cloud.google.com/storage/docs/access-control/signed-urls
	
30. You are creating a Google Kubernetes Engine (GKE) cluster with a cluster autoscaler feature enabled. You need to make sure that each node of the cluster will run a monitoring pod that sends container metrics to a third-party monitoring solution. What should you do?

	- A. Deploy the monitoring pod in a StatefulSet object.
	- B. Deploy the monitoring pod in a DaemonSet object.
	- C. Reference the monitoring pod in a Deployment object.
	- D. Reference the monitoring pod in a cluster initializer at the GKE cluster creation time.
	
	- **B**. Here we have a monitoring pod created when a new node created to match. This is a typical use of **DaemonSet**. A DaemonSet ensures that all (or some) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. Other typical use case of DaemonSet include: running a cluster storage daemon on everynode, running a logs collection daemon on every node. https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/


31. You want to send and consume Cloud Pub/Sub messages from your App Engine application. The Cloud Pub/Sub API is currently disabled. You will use a service account to authenticate your application to the API. You want to make sure your application can use Cloud Pub/Sub. What should you do?
	- A. Enable the Cloud Pub/Sub API in the API Library on the GCP Console.
	- B. Rely on the automatic enablement of the Cloud Pub/Sub API when the Service Account accesses it.
	- C. Use Deployment Manager to deploy your application. Rely on the automatic enablement of all APIs used by the application being deployed.
	- D. Grant the App Engine Default service account the role of Cloud Pub/Sub Admin. Have your application enable the API on the first connection to Cloud Pub/ Sub
	
	- **A**. To use any API service, the corresponding google API must be enabled first. In this case, the Cloud Pub/Sub API need to be enabled first. The easiest way is to **enable it in API library in GCP console**. You may also enable API programatically like `gcloud`. but there is no automatic enablement of APIs
	
32. You need to monitor resources that are distributed over different projects in Google Cloud Platform. You want to consolidate reporting **under the same Stackdriver Monitoring dashboard**. What should you do?
	- A. Use Shared VPC to connect all projects, and link Stackdriver to one of the projects.
	- B. For each project, create a Stackdriver account. In each project, create a service account for that project and grant it the role of Stackdriver Account Editor in all other projects.
	- C. Configure a single Stackdriver account, and link all projects to the same account.
	- D. Configure a single Stackdriver account for one of the projects. In Stackdriver, create a Group and add the other project names as criteria for that Group.
	
	- **C or D**. None of these are valid anymore because it is not stackdriver but cloud monitoring now. To consolidate multiple project in cloud monitoring, it is recommended to create a new project with monitoring scope, and add those projects you want to consolidate as monitored project. This is call scope expansion. Alternative, you can create monitoring in one project, and add other projects as monitored project to your scope. https://cloud.google.com/monitoring/settings/multiple-projects and https://cloud.google.com/monitoring/settings#concept-scope
	
33. You are deploying an application to a Compute Engine VM in a managed instance group. The application must be running at all times, but only a single instance of the VM should run per GCP project. How should you configure the instance group?
	- A. Set autoscaling to On, set the minimum number of instances to 1, and then set the maximum number of instances to 1.
	- B. Set autoscaling to Off, set the minimum number of instances to 1, and then set the maximum number of instances to 1.
	- C. Set autoscaling to On, set the minimum number of instances to 1, and then set the maximum number of instances to 2.
	- D. Set autoscaling to Off, set the minimum number of instances to 1, and then set the maximum number of instances to 2.
	
	- **A**. We want one and only one instance. Use autoscalling and set Min and Max instance to 1 will lock the instance number to one. And benefit from autoscalling recreate if instance crash. Auto scalling works independent from autohealing. https://cloud.google.com/compute/docs/autoscaler/managing-autoscalers#gcloud_2. https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/set-autoscaling. 

34. You want to verify the IAM users and roles assigned within a GCP project named my-project. What should you do?
	- A. Run gcloud iam roles list. Review the output section.
	- B. Run gcloud iam service-accounts list. Review the output section.
	- C. Navigate to the project and then to the IAM section in the GCP Console. Review the members and roles.
	- D. Navigate to the project and then to the Roles section in the GCP Console. Review the roles and status.
	
	- **C** To see IAM users and roles, go to *IAM & Admin > IAM*, can review members and roles assigned to project. *A* give you all roles availables. *B* give you the list of service accounts in this project. *D* list all roles but not users. 
	
35. You need to create a new billing account and then link it with an existing Google Cloud Platform project. What should you do?
	- A. Verify that you are Project Billing Manager for the GCP project. Update the existing project to link it to the existing billing account.
	- B. Verify that you are Project Billing Manager for the GCP project. Create a new billing account and link the new billing account to the existing project.
	- C. Verify that you are Billing Administrator for the billing account. Create a new project and link the new project to the existing billing account.
	- D. Verify that you are Billing Administrator for the billing account. Update the existing project to link it to the existing billing account.
	
	- **B** (Community Votes). This is a bit tricky question. It is not able what role, but what action you perform. **Neither** Project Billing Manager nor Billing Adminstrator role it self can create billing account. So we have to assumet they have other role combined or, they have someone to create billing account for them. Now take a look at the action, only **C** describe the correct process of creating billing account and them link to existing project. https://cloud.google.com/billing/docs/how-to/billing-access
	
36. You have one project called proj-sa where you manage all your service accounts. You want to be able to use a service account from this project to take snapshots of VMs running in another project called proj-vm. What should you do?
	- A. Download the private key from the service account, and add it to each VMs custom metadata.
	- B. Download the private key from the service account, and add the private key to each VM's SSH keys.
	- C. Grant the service account the IAM Role of Compute Storage Admin in the project called proj-vm.
	- D. When creating the VMs, set the service account's API scope for Compute Engine to read/write.
	
	- **C**. To take snapshots of VMs running in another project, you need to grant the service account that will take snapshots, the neccessary IAM role, which is Compute Storage Admin role, in the destination project (project-vm). So pick C. Do not download private key because it is unnecessary and risky

37. You created a Google Cloud Platform project with an App Engine application inside the project. You initially configured the application to be served from the us- central region. Now you want the application to be served from the asia-northeast1 region. What should you do?
	- A. Change the default region property setting in the existing GCP project to asia-northeast1.
	- B. Change the region property setting in the existing App Engine application from us-central to asia-northeast1.
	- C. Create a second App Engine application in the existing GCP project and specify asia-northeast1 as the region to serve your application.
	- D. Create a new GCP project and create an App Engine application inside this new project. Specify asia-northeast1 as the region to serve your application.
	
	- **D**. Each project can only have one App Engine. And you can not change location of App Engine once created. https://cloud.google.com/appengine/docs/flexible/managing-projects-apps-billing#create

38. You need to grant access for three users so that they can view and edit table data on a Cloud Spanner instance. What should you do?
	- A. Run gcloud iam roles describe roles/spanner.databaseUser. Add the users to the role.
	- B. Run gcloud iam roles describe roles/spanner.databaseUser. Add the users to a new group. Add the group to the role.
	- C. Run gcloud iam roles describe roles/spanner.viewer - -project my-project. Add the users to the role.
	- D. Run gcloud iam roles describe roles/spanner.viewer - -project my-project. Add the users to a new group. Add the group to the role.
	
	- **B**. Users need to view and edit data, so `roles/spanner.viewer` is not sufficient, instead need `roles/spanner.databaseUser`. It is also recommended to assign group to role instead of individual users

39. You create a new Google Kubernetes Engine (GKE) cluster and want to make sure that it always runs a supported and stable version of Kubernetes. What should you do?
	- A. Enable the Node Auto-Repair feature for your GKE cluster.
	- B. Enable the Node Auto-Upgrades feature for your GKE cluster.
	- C. Select the latest available cluster version for your GKE cluster.
	- D. Select ג€Container-Optimized OS (cos)ג€ as a node image for your GKE cluster.
	
	- **B**. When creating clusters with `latest` version do not provide auto upgrade. To do that, you **enable node auto0upgrades** to ensure cluster are up-to-date with the latest stable version. https://cloud.google.com/kubernetes-engine/versioning-and-upgrades

40. You have an instance group that you want to load balance. You want the load balancer to terminate the client SSL session. The instance group is used to serve a public web application over HTTPS. You want to follow Google-recommended practices. What should you do?
	- A. Configure an HTTP(S) load balancer.
	- B. Configure an internal TCP load balancer.
	- C. Configure an external SSL proxy load balancer.
	- D. Configure an external TCP proxy load balancer.
	
	- **A**. First of all, only HTTP(S) load balance can handle HTTP request. So there is no other options. On top of that, HTTP(s) load balancer will terminate SSL session, that is correct. SSL Proxy will end user SSL session, but will direct to backend using either SSL or TCP, not HTTP

41.  You have 32 GB of data in a single file that you need to upload to a Nearline Storage bucket. The WAN connection you are using is rated at 1 Gbps, and you are the only one on the connection. You want to use as much of the rated 1 Gbps as possible to transfer the file rapidly. How should you upload the file?
	 - A. Use the GCP Console to transfer the file instead of gsutil.
	 - B. Enable parallel composite uploads using gsutil on the file transfer.
	 - C. Decrease the TCP window size on the machine initiating the transfer.
	 - D. Change the storage class of the bucket from Nearline to Multi-Regional.
	
	 - **B**. The parallel composite uploads is the way to upload large files if network and disk speed are not limited. It divide files into up to 32 chuncks, upload to temporary objects, recreate it cloud storage and delete the temporary object
	
42. You've deployed a microservice called myapp1 to a Google Kubernetes Engine cluster using the YAML file containing plain password text. You need to refactor this configuration so that the database password is not stored in plain text. You want to follow Google-recommended practices. What should you do?
	- A. Store the database password inside the Docker image of the container, not in the YAML file.
	- B. Store the database password inside a Secret object. Modify the YAML file to populate the DB_PASSWORD environment variable from the Secret.
	- C. Store the database password inside a ConfigMap object. Modify the YAML file to populate the DB_PASSWORD environment variable from the ConfigMap.
	- D. Store the database password in a file inside a Kubernetes persistent volume, and use a persistent volume claim to mount the volume to the container.
	
	- **B**. Use Kubernetes Secrets to store confidential information and use ConfigMap to store non-confidential information
	
43. You are running an application on multiple virtual machines within a managed instance group and have autoscaling enabled. The autoscaling policy is configured so that additional instances are added to the group if the CPU utilization of instances goes above 80%. VMs are added until the instance group reaches its maximum limit of five VMs or until CPU utilization of instances lowers to 80%. The initial delay for HTTP health checks against the instances is **set to 30 seconds**. **The virtual machine instances take around three minutes to become available for users**. You observe that when the instance group autoscales, it adds more instances then necessary to support the levels of end-user traffic. You want to properly maintain instance group sizes when autoscaling. What should you do?
	- A. Set the maximum number of instances to 1.
	- B. Decrease the maximum number of instances to 3.
	- C. Use a TCP health check instead of an HTTP health check.
	- D. Increase the initial delay of the HTTP health check to 200 seconds.
	
	- **D**. The reason for having extra VMs instance is because HTTP health check at 30 seconds will fail due to unreadyness of new instances (after 3 min). To solve this we need to increase intial HTTP health check delay to 200 second > 180 second

44. You need to select and configure compute resources for a set of batch processing jobs. These jobs take around 2 hours to complete and are run nightly. You want to minimize service costs. What should you do?
	- A. Select Google Kubernetes Engine. Use a single-node cluster with a small instance type.
	- B. Select Google Kubernetes Engine. Use a three-node cluster with micro instance types.
	- C. Select Compute Engine. Use preemptible VM instances of the appropriate standard machine type.
	- D. Select Compute Engine. Use VM instance types that support micro bursting.
	
	- **C**. Consider the workload is 2 hour and run at night, Preemptible instances is the best option. It is much lower price, using excess compute engine resource (running at night so will be sufficient).  batch processing jobs can run on preemptible instances. If some of those instances stop during processing, the job slows but does not completely stop. Preemptible instances complete your batch processing tasks without placing additional workload on your existing instances and without requiring you to pay full price for additional normal instances. https://cloud.google.com/compute/docs/instances/preemptible
	
45. You recently deployed a new version of an application to App Engine and then discovered a bug in the release. You need to immediately revert to the prior version of the application. What should you do?
	- A. Run gcloud app restore.
	- B. On the App Engine page of the GCP Console, select the application that needs to be reverted and click Revert.
	- C. On the App Engine Versions page of the GCP Console, route 100% of the traffic to the previous version.
	- D. Deploy the original version as a separate application. Then go to App Engine settings and split traffic between applications so that the original version serves 100% of the requests.
	
	- **C**. There is no such thing as *Reverting a deployment* in App Engine. However, by using versioning and traffic split, we can route 100% traffic to old version to simulate a "Reverting" process


46. You deployed an App Engine application using gcloud app deploy, but it did not deploy to the intended project. You want to find out why this happened and where the application deployed. What should you do?
	- A. Check the app.yaml file for your application and check project settings.
	- B. Check the web-application.xml file for your application and check project settings.
	- C. Go to Deployment Manager and review settings for deployment of applications.
	- D. Go to Cloud Shell and run gcloud config list to review the Google Cloud configuration used for deployment.
	
	- **D**. Using `gcloud config list` giv eyou currently active configuration, such as account, project and environment. You can also run `gcloud config list project` to see what project you are in. Current project is where your deployment went
	
47. You want to configure 10 Compute Engine instances for availability when maintenance occurs. Your requirements state that these instances should attempt to automatically restart if they crash. Also, the instances should be highly available including during system maintenance. What should you do?
	- A. Create an instance template for the instances. Set the 'Automatic Restart' to on. Set the 'On-host maintenance' to Migrate VM instance. Add the instance template to an instance group.
	- B. Create an instance template for the instances. Set 'Automatic Restart' to off. Set 'On-host maintenance' to Terminate VM instances. Add the instance template to an instance group.
	- C. Create an instance group for the instances. Set the 'Autohealing' health check to healthy (HTTP).
	- D. Create an instance group for the instance. Verify that the 'Advanced creation options' setting for 'do not retry machine creation' is set to off.
	
	- **A**. When creating instance template, we can specify "Automatic Restart" to ON (default) so instance will restart when they crash. Setting on-host maintenance to "Migrate" (Default) will live migrate instance instead of terminating. Note that here we talk about VM instances, not App running inside of VM. So we talk about ionstance template, not Autohealing in instance group. 

48. You host a static website on Cloud Storage. Recently, you began to include links to PDF files on this site. Currently, when users click on the links to these PDF files, their browsers prompt them to save the file onto their local system. Instead, you want the clicked PDF files to be displayed within the browser window directly, without prompting the user to save the file locally. What should you do?
	- A. Enable Cloud CDN on the website frontend.
	- B. Enable 'Share publicly' on the PDF file objects.
	- C. Set Content-Type metadata to application/pdf on the PDF file objects.
	- D. Add a label to the storage bucket with a key of Content-Type and value of application/pdf.
	
	- **C**. This is not about if resource is accessible or not. It is about how to access the resrouce. *Content-Type* meta data will allow browser to determine how to serve the resource. To Serve PDF file in brwoser windows we need "Content-Type: application/pdf". To do that, go to the cloud storage, Edit Bucket and go to "Website" tab, In the "Website Configuration" section, select the "Serve objects with this content type" option and enter "application/pdf" in the text field. *D* is incorrect because Labels are used for organizing resources, while metadata is used to provide information about the data itself.


49. You have a virtual machine that is currently configured with 2 vCPUs and 4 GB of memory. It is running out of memory. You want to upgrade the virtual machine to have 8 GB of memory. What should you do?
	- A. Rely on live migration to move the workload to a machine with more memory.
	- B. Use gcloud to add metadata to the VM. Set the key to required-memory-size and the value to 8 GB.
	- C. Stop the VM, change the machine type to n1-standard-8, and start the VM.
	- D. Stop the VM, increase the memory to 8 GB, and start the VM.
	
	- **D**. To change the machine type, you need to stop the VM first. It is OK to change the machine type or Memory after you stop the VM. *D* is correct. `n1-standard-8` come with 8 vCPU and 30G memory which is too much

50. You have production and test workloads that you want to deploy on Compute Engine. Production VMs need to be in a different subnet than the test VMs. All the
VMs must be able to reach each other over Internal IP without creating additional routes. You need to set up VPC and the 2 subnets. Which configuration meets these requirements?
	- A. Create a single custom VPC with 2 subnets. Create each subnet in a different region and with a different CIDR range.
	- B. Create a single custom VPC with 2 subnets. Create each subnet in the same region and with the same CIDR range.
	- C. Create 2 custom VPCs, each with a single subnet. Create each subnet in a different region and with a different CIDR range.
	- D. Create 2 custom VPCs, each with a single subnet. Create each subnet in the same region and with the same CIDR range.
	
	- **A**. Internal IP communication with additional routing = Same VPC. In a single VPC, primary and secondary ranges for subnets cannot overlap therefore A is correct. https://cloud.google.com/vpc/docs/using-vpc#subnet-rules

51. You need to create an autoscaling managed instance group for an HTTPS web application. You want to make sure that unhealthy VMs are recreated. What should you do?
	- A. Create a health check on port 443 and use that when creating the Managed Instance Group.
	- B. Select Multi-Zone instead of Single-Zone when creating the Managed Instance Group.
	- C. In the Instance Template, add the label 'health-check'.
	- D. In the Instance Template, add a startup script that sends a heartbeat to the metadata server.

	- **A**. Port 443 is responsible for `SSL, HTTPS and HTTP2` where as PORT 80 is for `TCP and HTTP`
	
52. Your company has a Google Cloud Platform project that uses BigQuery for data warehousing. Your data science team changes frequently and has few members.
You need to allow members of this team to perform queries. You want to follow Google-recommended practices. What should you do?
	- A. 1. Create an IAM entry for each data scientist's user account. 2. Assign the BigQuery jobUser role to the group.
	- B. 1. Create an IAM entry for each data scientist's user account. 2. Assign the BigQuery dataViewer user role to the group.
	- C. 1. Create a dedicated Google group in Cloud Identity. 2. Add each data scientist's user account to the group. 3. Assign the BigQuery jobUser role to the group.
	- D. 1. Create a dedicated Google group in Cloud Identity. 2. Add each data scientist's user account to the group. 3. Assign the BigQuery dataViewer user role to the group.
	
	- **C**. DataViewer cannot perform job query and it is a necessary task for data scientist. Job User can perform Query. https://cloud.google.com/bigquery/docs/access-control#bigquery.dataViewer 

53. Your company has a 3-tier solution running on Compute Engine （1， 2， 3）. Each tier has a service account that is associated with all instances within it. You need to enable communication on TCP port 8080 between tiers as follows:

	 * Instances in tier #1 must communicate with tier #2.
	 * Instances in tier #2 must communicate with tier #3.
		
	 * What should you do?
	
		 * A. 1. Create an ingress firewall rule with the following settings: ג€Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.2.0/24) ג€¢ Protocols: allow all 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.1.0/24) ג€¢ Protocols: allow all
		 * B. 1. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #2 service account ג€¢ Source filter: all instances with tier #1 service account ג€¢ Protocols: allow TCP:8080 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #3 service account ג€¢ Source filter: all instances with tier #2 service account ג€¢ Protocols: allow TCP: 8080
		 * C. 1. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #2 service account ג€¢ Source filter: all instances with tier #1 service account ג€¢ Protocols: allow all 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #3 service account ג€¢ Source filter: all instances with tier #2 service account ג€¢ Protocols: allow all
		 * D. 1. Create an egress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.2.0/24) ג€¢ Protocols: allow TCP: 8080 2. Create an egress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.1.0/24) ג€¢ Protocols: allow TCP: 8080
		
		 * **B**. First of all, the requirement want communication on TCP port 8080, not all Port. So **Protocols** should be `allow TCP: 8080`. And from tier-1 to Tier-2, we want Ingress rule with target Tier 2 and source Tier 1. From Tier-2 to Tier-3 we want Ingress target Tier-3 and source Tier-2
	
54. You are given a project with a single Virtual Private Cloud (VPC) and a single subnetwork in the us-central1 region. There is a Compute Engine instance hosting an application in this subnetwork. You need to deploy a new instance in the same project in the europe-west1 region. This new instance needs access to the application. You want to follow Google-recommended practices. What should you do?
	- A. 1. Create a subnetwork in the same VPC, in europe-west1. 2. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.
	- B. 1. Create a VPC and a subnetwork in europe-west1. 2. Expose the application with an internal load balancer. 3. Create the new instance in the new subnetwork and use the load balancer's address as the endpoint.
	- C. 1. Create a subnetwork in the same VPC, in europe-west1. 2. Use Cloud VPN to connect the two subnetworks. 3. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.
	- D. 1. Create a VPC and a subnetwork in europe-west1. 2. Peer the 2 VPCs. 3. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.
	
	- **A**. VPC can have subnetwork in different region and instance within the same VPC can communicate with private address, regardless of its region. There is no need to create additional VPC, using load balancer or using Cloud VPN. Cloud VPN connect your peer network to VPC
	
55. Your projects incurred more costs than you expected last month. Your research reveals that a development GKE container emitted a huge number of logs, which resulted in higher costs. You want to disable the logs quickly using the minimum number of steps. What should you do?
	- A. 1. Go to the Logs ingestion window in Stackdriver Logging, and disable the log source for the GKE container resource.
	- B. 1. Go to the Logs ingestion window in Stackdriver Logging, and disable the log source for the GKE Cluster Operations resource.
	- C. 1. Go to the GKE console, and delete existing clusters. 2. Recreate a new cluster. 3. Clear the option to enable legacy Stackdriver Logging.
	- D. 1. Go to the GKE console, and delete existing clusters. 2. Recreate a new cluster. 3. Clear the option to enable legacy Stackdriver Monitoring.
	
	- **A**. No need to delete and recreate cluster. The high cost is due to large amount of logs from **GKE container**, so A is correct
	
56. You have a website hosted on App Engine standard environment. You want 1% of your users to see a new test version of the website. You want to minimize complexity. What should you do?
	- A. Deploy the new version in the same application and use the --migrate option.
	- B. Deploy the new version in the same application and use the --splits option to give a weight of 99 to the current version and a weight of 1 to the new version.
	- C. Create a new App Engine application in the same project. Deploy the new version in that application. Use the App Engine library to proxy 1% of the requests to the new version.
	- D. Create a new App Engine application in the same project. Deploy the new version in that application. Configure your network load balancer to send 1% of the traffic to that new application.
	
	- **B**. To split/load balance traffic in App Engine, we use versioning and traffic splitting with same application. You cannot create multiple App Engine in the same project


57. You have a web application deployed as a managed instance group. You have a new version of the application to gradually deploy. Your web application is currently receiving live web traffic. You want to ensure that the available capacity does not decrease during the deployment. What should you do?
	- A. Perform a rolling-action start-update with maxSurge set to 0 and maxUnavailable set to 1.
	- B. Perform a rolling-action start-update with maxSurge set to 1 and maxUnavailable set to 0.
	- C. Create a new managed instance group with an updated instance template. Add the group to the backend service for the load balancer. When all instances in the new managed instance group are healthy, delete the old managed instance group.
	- D. Create a new instance template with the new application version. Update the existing managed instance group with the new instance template. Delete the instances in the managed instance group to allow the managed instance group to recreate the instance using the new instance template.
	
	- **B**. The command `gcloud compute instance-groups managed rolling-action start-update` is used to update instances in managed instance group. To ensure global availability during update, we set `maxUnavailable` to 0. To ensure additional instance can be created (gradually with low cost), we set `maxSurge` to 1. The `maxSurge` parameter controls the maximum number of new instances that can be created above the desired number of instances during the update process. Answer C might work, but it is the hard and high cost way.
	
58. You are building an application that stores relational data from users. Users across the globe will use this application. Your CTO is concerned about the scaling requirements because the size of the user base is unknown. You need to implement a database solution that can scale with your user growth with minimum configuration changes. Which storage solution should you use?
	- A. Cloud SQL
	- B. Cloud Spanner
	- C. Cloud Firestore
	- D. Cloud Datastore
	
	- **B**. Cloud Spanner is a relational database that is best for large, global and high scalable data. The data above is relational, globally used and user base is unknown. So cloud spanner is the best option. Cloud SQL is similar to cloud spanner but usually used with smaller, less global data that do not need as high scalability as Cloud Spanner. Firestore and Datastore are noSQL database 
	
59. You are the organization and billing administrator for your company. The engineering team has the Project Creator role on the organization. You do not want the engineering team to be able to link projects to the billing account. Only the finance team should be able to link a project to a billing account, but they should not be able to make any other changes to projects. What should you do?
	- A. Assign the finance team only the Billing Account User role on the billing account.
	- B. Assign the engineering team only the Billing Account User role on the billing account.
	- C. Assign the finance team the Billing Account User role on the billing account and the Project Billing Manager role on the organization.
	- D. Assign the engineering team the Billing Account User role on the billing account and the Project Billing Manager role on the organization.
	
	- **C** (Debating). The questions phrase poorly but **C** is the best choice. Billing Account User allow you to view billing account and nothing more. Billing Account User + Project Creator: create project and link to that billing account. Billing Account User + Project Billing Manager: link and unlink projects on that billing account. So here don't give engineering team this role. Finance team would need Billing Account User and Project Billing Manager role. (A seems to be insufficient)

60. You have an application running in Google Kubernetes Engine (GKE) with cluster autoscaling enabled. The application exposes a TCP endpoint. There are several replicas of this application. You have a Compute Engine instance in the same region, but in another Virtual Private Cloud (VPC), called gce-network, that has no overlapping IP ranges with the first VPC. This instance needs to connect to the application on GKE. You want to minimize effort. What should you do?
	- A. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Set the service's externalTrafficPolicy to Cluster. 3. Configure the Compute Engine instance to use the address of the load balancer that has been created.
	- B. 1. In GKE, create a Service of type NodePort that uses the application's Pods as backend. 2. Create a Compute Engine instance called proxy with 2 network interfaces, one in each VPC. 3. Use iptables on this instance to forward traffic from gce-network to the GKE nodes. 4. Configure the Compute Engine instance to use the address of proxy in gce-network as endpoint.
	- C. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Add an annotation to this service: cloud.google.com/load-balancer-type: Internal 3. Peer the two VPCs together. 4. Configure the Compute Engine instance to use the address of the load balancer that has been created.
	- D. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Add a Cloud Armor Security Policy to the load balancer that whitelists the internal IPs of the MIG's instances. 3. Configure the Compute Engine instance to use the address of the load balancer that has been created.
	
	- **A or C**. Both A and C work, it is a matter of which one is easier. *A* use a loadBlancer with external proxy. It create external communication. *C* use load balancer with VPC peering, it use internal communication. This question metioned two VPC with no overlapping ranges, which is like an indicator for a perfect candidate of VPC peering. So **C** is preferred over *A*


61. Your organization is a financial company that needs to store audit log files for 3 years. Your organization has hundreds of Google Cloud projects. You need to implement a cost-effective approach for log file retention. What should you do?
	- A. Create an export to the sink that saves logs from Cloud Audit to BigQuery.
	- B. Create an export to the sink that saves logs from Cloud Audit to a Coldline Storage bucket.
	- C. Write a custom script that uses logging API to copy the logs from Stackdriver logs to BigQuery.
	- D. Export these logs to Cloud Pub/Sub and write a Cloud Dataflow pipeline to store logs to Cloud SQL.
	
	- **B**. We want cost-effective long term (3 yrs) storage. Coldline Storage bucket is the best option, we can use Sink to export to Coldline cloud storage. **Sink** control how Cloud Logging routes logs. You can route logs to 1. Cloud logging bucket. 2. Different GCP project. 3. Pub.Sub - for 3rd party integration. 4. BigQuery - for analysis 5. Cloud Storage - for inexpensive, long-term storage as JSON file
	
62. You want to run a single caching HTTP reverse proxy on GCP for a latency-sensitive website. This specific reverse proxy consumes almost no CPU. You want to have a 30-GB in-memory cache, and need an additional 2 GB of memory for the rest of the processes. You want to minimize cost. How should you run this reverse proxy?
	- A. Create a Cloud Memorystore for Redis instance with 32-GB capacity.
	- B. Run it on Compute Engine, and choose a custom instance type with 6 vCPUs and 32 GB of memory.
	- C. Package it in a container image, and run it on Kubernetes Engine, using n1-standard-32 instances as nodes.
	- D. Run it on Compute Engine, choose the instance type n1-standard-1, and add an SSD persistent disk of 32 GB.
	
	- **A**. The project is a latency-sensitive website, consume no CPU but heavily rely on in-memory cache. Redis (Cloud Memorystore) is a greate candidate. Memorystore for Redis provides low latency access. This is the best options. choosing VM with 6vCPU and 32GB memory may cost a bit less but waste CPU resource and does not provide low latency as Memorystore. https://cloud.google.com/memorystore/docs/redis/redis-overview#what_its_good_for
	
63. You are hosting an application on bare-metal servers in your own data center. The application needs access to Cloud Storage. However, security policies prevent the servers hosting the application from having public IP addresses or access to the internet. You want to follow Google-recommended practices to provide the application with access to Cloud Storage. What should you do?
	- A. 1. Use nslookup to get the IP address for storage.googleapis.com. 2. Negotiate with the security team to be able to give a public IP address to the servers. 3. Only allow egress traffic from those servers to the IP addresses for storage.googleapis.com.
	- B. 1. Using Cloud VPN, create a VPN tunnel to a Virtual Private Cloud (VPC) in Google Cloud. 2. In this VPC, create a Compute Engine instance and install the Squid proxy server on this instance. 3. Configure your servers to use that instance as a proxy to access Cloud Storage.
	- C. 1. Use Migrate for Compute Engine (formerly known as Velostrata) to migrate those servers to Compute Engine. 2. Create an internal load balancer (ILB) that uses storage.googleapis.com as backend. 3. Configure your new instances to use this ILB as proxy.
	- D. 1. Using Cloud VPN or Interconnect, create a tunnel to a VPC in Google Cloud. 2. Use Cloud Router to create a custom route advertisement for 199.36.153.4/30. Announce that network to your on-premises network through the VPN tunnel. 3. In your on-premises network, configure your DNS server to resolve *.googleapis.com as a CNAME to restricted.googleapis.com.
	
	- **D**. Anytime you want to connect on-permise to google cloud, especially without public IP, Cloud VPN or Cloud Interconnect are the answer. You use cloud router to route to your on-permise server. There is no need to install anything extra. https://cloud.google.com/vpc/docs/configure-private-google-access-hybrid
	

	
64. You want to deploy an application on Cloud Run that processes messages from a Cloud Pub/Sub topic. You want to follow Google-recommended practices. What should you do?
	- A. 1. Create a Cloud Function that uses a Cloud Pub/Sub trigger on that topic. 2. Call your application on Cloud Run from the Cloud Function for every message.
	- B. 1. Grant the Pub/Sub Subscriber role to the service account used by Cloud Run. 2. Create a Cloud Pub/Sub subscription for that topic. 3. Make your application pull messages from that subscription.
	- C. 1. Create a service account. 2. Give the Cloud Run Invoker role to that service account for your Cloud Run application. 3. Create a Cloud Pub/Sub subscription that uses that service account and uses your Cloud Run application as the push endpoint.
	- D. 1. Deploy your application on Cloud Run on GKE with the connectivity set to Internal. 2. Create a Cloud Pub/Sub subscription for that topic. 3. In the same Google Kubernetes Engine cluster as your application, deploy a container that takes the messages and sends them to your application.
	
	- **C**. As per https://cloud.google.com/run/docs/tutorials/pubsub#integrating-pubsub, The way to intergrate Pub/Sub with cloud run, you first create a service accounot, then create Cloud Run app using that service account. Finally, you want Pub/Sub to **PUSH** to cloud run as endpoint. This match C. *B* might work, but ask cloud run to pull from Pub/Sub means you cannot scale to zero, cloud run has to activly running
	
65. You need to deploy an application, which is packaged in a container image, in a new project. The application exposes an HTTP endpoint and receives very few requests per day. You want to minimize costs. What should you do?
	- A. Deploy the container on Cloud Run.
	- B. Deploy the container on Cloud Run on GKE.
	- C. Deploy the container on App Engine Flexible.
	- D. Deploy the container on GKE with cluster autoscaling and horizontal pod autoscaling enabled.
	
	- **A**. Cloud run is the only options above that potentially scale to zero. You can deploy App itself, or a container image on Cloud Run. So **A** works best. 

66. Your company has an existing GCP organization with hundreds of projects and a billing account. Your company recently acquired another company that also has hundreds of projects and its own billing account. You would like to consolidate all GCP costs of both GCP organizations onto a single invoice. You would like to consolidate all costs as of tomorrow. What should you do?
	- A. Link the acquired company's projects to your company's billing account.
	- B. Configure the acquired company's billing account and your company's billing account to export the billing data into the same BigQuery dataset.
	- C. Migrate the acquired company's projects into your company's GCP organization. Link the migrated projects to your company's billing account.
	- D. Create a new GCP organization and a new billing account. Migrate the acquired company's projects and your company's projects into the new GCP organization and link the projects to the new billing account.
	
	- **A**. Link acquired company's projects to your company's billing account is the fastest way. You cannot directly link your billing account to other organization, you can first grant user in other organization the permission to your billing account. Then, that user will have ability to update billing account on the other organization. This will be faster than migrating all projects then link. https://fargyle.medium.com/google-cloud-platform-cross-org-billing-41c5db8fefa6


67. You built an application on Google Cloud that uses Cloud Spanner. Your support team needs to monitor the environment but should not have access to table data.
You need a streamlined solution to grant the correct permissions to your support team, and you want to follow Google-recommended practices. What should you do?
	- A. Add the support team group to the roles/monitoring.viewer role
	- B. Add the support team group to the roles/spanner.databaseUser role.
	- C. Add the support team group to the roles/spanner.databaseReader role.
	- D. Add the support team group to the roles/stackdriver.accounts.viewer role.
	
	- **A**. The audit team should only access monitoring related information. So `roles/monitoring.viewer` is sufficient and enougth. No need to access any `spanner` role. `stackdriver.accounts.viewer` allows you view stackdriver account information, it is not related to the environment
	
68. For analysis purposes, you need to send all the logs from all of your Compute Engine instances to a BigQuery dataset called platform-logs. You have already installed the Cloud Logging agent on all the instances. You want to minimize cost. What should you do?
	- A. 1. Give the BigQuery Data Editor role on the platform-logs dataset to the service accounts used by your instances. 2. Update your instances' metadata to add the following value: logs-destination: bq://platform-logs.
	- B. 1. In Cloud Logging, create a logs export with a Cloud Pub/Sub topic called logs as a sink. 2. Create a Cloud Function that is triggered by messages in the logs topic. 3. Configure that Cloud Function to drop logs that are not from Compute Engine and to insert Compute Engine logs in the platform-logs dataset.
	- C. 1. In Cloud Logging, create a filter to view only Compute Engine logs. 2. Click Create Export. 3. Choose BigQuery as Sink Service, and the platform-logs dataset as Sink Destination.
	- D. 1. Create a Cloud Function that has the BigQuery User role on the platform-logs dataset. 2. Configure this Cloud Function to create a BigQuery Job that executes this query: INSERT INTO dataset.platform-logs (timestamp, log) SELECT timestamp, log FROM compute.logs WHERE timestamp > DATE_SUB(CURRENT_DATE(), INTERVAL 1 DAY) 3. Use Cloud Scheduler to trigger this Cloud Function once a day.
	
	- **C**. Use Cloud Logging agent with a sink that streams to BigQuery is the simplest way. Also, BQ charge by data and no need to Pub/Sub every data from all instances and drop some of them.
	
69. You are using Deployment Manager to create a Google Kubernetes Engine cluster. Using the same Deployment Manager deployment, you also want to create a
DaemonSet in the kube-system namespace of the cluster. You want a solution that uses the fewest possible services. What should you do?
	- A. Add the cluster's API as a new Type Provider in Deployment Manager, and use the new type to create the DaemonSet.
	- B. Use the Deployment Manager Runtime Configurator to create a new Config resource that contains the DaemonSet definition.
	- C. With Deployment Manager, create a Compute Engine instance with a startup script that uses kubectl to create the DaemonSet.
	- D. In the cluster's definition in Deployment Manager, add a metadata that has kube-system as key and the DaemonSet manifest as value.
	
	- **A**. A type provider exposes all of the resources of a third-party API to Deployment Manager as base types that you can use in your configurations. If you want to use an API that is not automatically provided by Google with Deployment Manager, you must add the API as a type provider. Here we add proper cluster's API as type provider, then we can create DaemonSet. It is easier than creating your own config


70. You are building an application that will run in your data center. The application will use Google Cloud Platform (GCP) services like AutoML. You created a service account that has appropriate access to AutoML. You need to enable authentication to the APIs from your on-premises environment. What should you do?
	- A. Use service account credentials in your on-premises application.
	- B. Use gcloud to create a key file for the service account that has appropriate permissions.
	- C. Set up direct interconnect between your data center and Google Cloud Platform to enable authentication for your on-premises applications.
	- D. Go to the IAM & admin console, grant a user account permissions similar to the service account permissions, and use this user account for authentication from your data center.
 
	- **B**. To use service account outside of Google Cloud, you must establish identity of service account, which is a public/private key pair. The command is `gcloud iam service-accounts keys create KEY_FILE --iam-account=SA_NAME PROJECT_ID` https://cloud.google.com/iam/docs/keys-create-delete 

71. You are using Container Registry to centrally store your company's container images in a separate project. In another project, you want to create a Google
Kubernetes Engine (GKE) cluster. You want to ensure that Kubernetes can download images from Container Registry. What should you do?
	- A. In the project where the images are stored, grant the Storage Object Viewer IAM role to the service account used by the Kubernetes nodes.
	- B. When you create the GKE cluster, choose the Allow full access to all Cloud APIs option under 'Access scopes'.
	- C. Create a service account, and give it access to Cloud Storage. Create a P12 key for this service account and use it as an imagePullSecrets in Kubernetes.
	- D. Configure the ACLs on each image in Cloud Storage to give read-only access to the default Compute Engine service account.
	
	- **A**. Google Container Registry use Cloud Storage Bucket under the hood. So this is about IAM of GKE cluster accessing Cloud Storage in another project. In Cloud storage, grant GKE service account correct permission++


72. You deployed a new application inside your Google Kubernetes Engine cluster with one Deploymentn Pod and one Service Pod. You check the status of the deployed pods and notice that one of them is still in PENDING status. (myapp-deployment-58ddbbb995-lp86m). You want to find out why the pod is stuck in **pending** status. What should you do?
	- A. Review details of the myapp-service Service object and check for error messages.
	- B. Review details of the myapp-deployment Deployment object and check for error messages.
	- C. Review details of myapp-deployment-58ddbbb995-lp86m Pod and check for warning messages.
	- D. View logs of the container in myapp-deployment-58ddbbb995-lp86m pod and check for warning messages.
	
	- **C**. The first step in debugging a pod is taking a look at it using `kubectl describe pods ${POD_NAME}`. We reviews the details of that pod **directly** using this command and check for warning message. If a Pod is stuck in Pending it means that it can not be scheduled onto a node. Generally this is because there are insufficient resources of one type or another that prevent scheduling. https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/#debugging-pods

73. You are setting up a Windows VM on Compute Engine and want to make sure you can log in to the VM via RDP. What should you do?
	- A. After the VM has been created, use your Google Account credentials to log in into the VM.
	- B. After the VM has been created, use gcloud compute reset-windows-password to retrieve the login credentials for the VM.
	- C. When creating the VM, add metadata to the instance using 'windows-password' as the key and a password as the value.
	- D. After the VM has been created, download the JSON private key for the default Compute Engine service account. Use the credentials in the JSON file to log in to the VM.
	
	- **B**. Windows VM need windows account/credential. `gcloud compute reset-windows-password` allows a user to reset and retrieve a password for a Windows virtual machine instance. If the Windows account does not exist, this command will cause the account to be created and the password for that new account will be returned. https://cloud.google.com/sdk/gcloud/reference/compute/reset-windows-password
	
74. You want to configure an SSH connection to a single Compute Engine instance for users in the dev1 group. This instance is the only resource in this particular
Google Cloud Platform project that the dev1 users should be able to connect to. What should you do?	
	- A. Set metadata to enable-oslogin=true for the instance. Grant the dev1 group the compute.osLogin role. Direct them to use the Cloud Shell to ssh to that instance.
	- B. Set metadata to enable-oslogin=true for the instance. Set the service account to no service account for that instance. Direct them to use the Cloud Shell to ssh to that instance.
	- C. Enable block project wide keys for the instance. Generate an SSH key for each user in the dev1 group. Distribute the keys to dev1 users and direct them to use their third-party tools to connect.
	- D. Enable block project wide keys for the instance. Generate an SSH key and associate the key with that instance. Distribute the key to dev1 users and direct them to use their third-party tools to connect.
	
	- **A**. OS Login enables you to control access to VM instance (not for Windows VM or SQL VM) based on **IAM permission** (including SSH). This need to be enabled. Then you need to define the IAM role, `compute.osLogin` for dedicated group. After that they can use Cloud Shell to SSH. Note that you can specify if you want OS Login at project level or at instance level. https://cloud.google.com/compute/docs/oslogin/set-up-oslogin
	
75. You need to produce a list of the enabled Google Cloud Platform APIs for a GCP project using the gcloud command line in the Cloud Shell. The project name is my-project. What should you do?
	- A. Run gcloud projects list to get the project ID, and then run gcloud services list --project <project ID>.
	- B. Run gcloud init to set the current project to my-project, and then run gcloud services list --available.
	- C. Run gcloud info to view the account value, and then run gcloud services list --account <Account>.
	- D. Run gcloud projects describe <project ID> to verify the project value, and then run gcloud services list --available.
	
	- **A**. You can either get project ID using `gcloud projects list` and use project ID to run service list `gcloud service list --project PROJECT_ID`. OR, you can use `gcloud init` to set current project to my-project, and run `gcloud service list` for current project. However, the `--available` flag returns all available services, not only those enabled. https://cloud.google.com/sdk/gcloud/reference/services/list#--available

76. You are building a new version of an application hosted in an **App Engine environment**. You want to test the new version with 1% of users before you completely switch your application over to the new version. What should you do?
	- A. Deploy a new version of your application in Google Kubernetes Engine instead of App Engine and then use GCP Console to split traffic.
	- B. Deploy a new version of your application in a Compute Engine instance instead of App Engine and then use GCP Console to split traffic.
	- C. Deploy a new version as a separate app in App Engine. Then configure App Engine using GCP Console to split traffic between the two apps.
	- D. Deploy a new version of your application in App Engine. Then go to App Engine settings in GCP Console and split traffic between the current version and newly deployed versions accordingly.
	
	- **D**. First, we are using App Engine. So no need to involve any other resource, just stick to App Engine. App Engine support versioning and traffic split. You can use traffic splitting to specify a percentage distribution of traffic across two or more of the versions within a service. So here we use the same App Engine Env, with different versioning and split the traffic across. https://cloud.google.com/appengine/docs/legacy/standard/python/splitting-traffic
	
77. You need to provide a cost estimate for a Kubernetes cluster using the GCP pricing calculator for Kubernetes. Your workload requires high IOPs, and you will also be using disk snapshots. You start by entering the number of nodes, average hours, and average days. What should you do next?
	- A. Fill in local SSD. Fill in persistent disk storage and snapshot storage.
	- B. Fill in local SSD. Add estimated cost for cluster management.
	- C. Select Add GPUs. Fill in persistent disk storage and snapshot storage.
	- D. Select Add GPUs. Add estimated cost for cluster management.
	
	- **A**. First of all, IOPS stands for Input/Output per second. For High IOPS you want to use local SSD because it is physically attaced to server with superior performance, low latency. https://cloud.google.com/compute/docs/disks/local-ssd. However, local SSD do not support disk snapshot, so also need to fill in persistent disk. https://cloud.google.com/compute/docs/disks/create-snapshots

78. You are using Google Kubernetes Engine with autoscaling enabled to host a new application. You want to expose this new application to the public, using HTTPS on a public IP address. What should you do?
	- A. Create a Kubernetes Service of type NodePort for your application, and a Kubernetes Ingress to expose this Service via a Cloud Load Balancer.
	- B. Create a Kubernetes Service of type ClusterIP for your application. Configure the public DNS name of your application using the IP of this Service.
	- C. Create a Kubernetes Service of type NodePort to expose the application on port 443 of each node of the Kubernetes cluster. Configure the public DNS name of your application with the IP of every node of the cluster to achieve load-balancing.
	- D. Create a HAProxy pod in the cluster to load-balance the traffic to all the pods of the application. Forward the public traffic to HAProxy with an iptable rule. Configure the DNS name of your application using the public IP of the node HAProxy is running on.
	
	- **A**. For public access via HTTPS in GKE, you want to use **Kubernetes Ingress** which is a service for HTTP(S) Cloud Load Balancing. Kubernetes Ingress use backend service associated with a type `NodePort`. There is another publically accessible Cloud load balancing - Network load balancer, which is for TCP/UDP connection. https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer

79. You need to enable traffic between multiple groups of Compute Engine instances that are currently running two different GCP projects. Each group of Compute
Engine instances is running in its own VPC. What should you do?
	- A. Verify that both projects are in a GCP Organization. Create a new VPC and add all instances.
	- B. Verify that both projects are in a GCP Organization. Share the VPC from one project and request that the Compute Engine instances in the other project use this shared VPC.
	- C. Verify that you are the Project Administrator of both projects. Create two new VPCs and add all instances.
	- D. Verify that you are the Project Administrator of both projects. Create a new VPC and add all instances.
	
	- **B**. To enable traffic between two GCP projects, there are two options: Shared VPC or VPC peering. Shared VPC used one VPC in one project, shared to another project for used. So two projects are running under same VPC. This require two project to be in the same organization. VPC peering connect two VPC. Unlike shared VPC which need to stay in the same organization, VPC peering can be withing orgization or in different organization. This question only have Shared VPC option available 

80. You want to add a new auditor to a Google Cloud Platform project. The auditor should be allowed to read, but not modify, all project items.
How should you configure the auditor's permissions?
	- A. Create a custom role with view-only project permissions. Add the user's account to the custom role.
	- B. Create a custom role with view-only service permissions. Add the user's account to the custom role.
	- C. Select the built-in IAM project Viewer role. Add the user's account to this role.
	- D. Select the built-in IAM service Viewer role. Add the user's account to this role.
	
	- **C** is most voted through some people go for **A**. First of all, *A* and *C* are pertty much equal. with principle of leastprivilege should be A, with recomendation of not using custom roles becasue they are not maintained by gcp it should be C. Google suggest not to use basic role in Production which is where auditor works. It may seems like A is correct, but consider Auditor need view access to everything in a project, create custom role and add permission one by one is impossible. So **C** is the practical answer, which fit in "no other alternative" justification.

81.  You are operating a Google Kubernetes Engine (GKE) cluster for your company where different teams can run non-production workloads. Your Machine Learning
(ML) team needs access to Nvidia Tesla P100 GPUs to train their models. You want to minimize effort and cost. What should you do?
	 - A. Ask your ML team to add the `accelerator: gpu` annotation to their pod specification.
	 - B. Recreate all the nodes of the GKE cluster to enable GPUs on all of them.
	 - C. Create your own Kubernetes cluster on top of Compute Engine with nodes that have GPUs. Dedicate this cluster to your ML team.
	 - D. Add a new, GPU-enabled, node pool to the GKE cluster. Ask your ML team to add the `cloud.google.com/gke -accelerator: nvidia-tesla-p100` nodeSelector to their pod specification.
	
	 - **D**. You can use GPU in GKE, and you do not need to specify that at cluster level, however, you cannot add GPU to existing node pools and GPU node is not live migrated. Therefore, you need to **Add a new pool** with GPU-enabled. You can specify the type of GPU in pod specification. https://cloud.google.com/kubernetes-engine/docs/how-to/gpus
	 
82. Your VMs are running in a subnet that has a subnet mask of 255.255.255.240. The current subnet has no more free IP addresses and you require an additional
10 IP addresses for new VMs. The existing and new VMs should all be able to reach each other without additional routes. What should you do?
	- A. Use gcloud to expand the IP range of the current subnet.
	- B. Delete the subnet, and recreate it using a wider range of IP addresses.
	- C. Create a new project. Use Shared VPC to share the current network with the new project.
	- D. Create a new subnet with the same starting IP but a wider range to overwrite the current subnet.

	- **A**. You can expand IP range of the subnet to obtain more IP address. You use `gcloud compute networks subnets expand-ip-range` command. https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/expand-ip-range. Refer to CIDR chart. Number of Host = 2^(32-/notation number) - 2

83. Your organization uses G Suite for communication and collaboration. All users in your organization have a G Suite account. You want to grant some G Suite users access to your Cloud Platform project. What should you do?
	- A. Enable Cloud Identity in the GCP Console for your domain.
	- B. Grant them the required IAM roles using their G Suite email address.
	- C. Create a CSV sheet with all users' email addresses. Use the gcloud command line tool to convert them into Google Cloud Platform accounts.
	- D. In the G Suite console, add the users to a special group called cloud-console-users@yourdomain.com. Rely on the default behavior of the Cloud Platform to grant users access if they are members of this group.

	- **B**. An organization resource is available for Google Workspace and Cloud Identity customer. To grant G Suite users access to a Cloud Platform project, you should use their G Suite email addresses to grant them the required IAM roles.

84. You have a Google Cloud Platform account with access to both production and development projects. You need to create an automated process to list all compute instances in development and production projects on a daily basis. What should you do?
	- A. Create two configurations using gcloud config. Write a script that sets configurations as active, individually. For each configuration, use gcloud compute instances list to get a list of compute resources.
	- B. Create two configurations using gsutil config. Write a script that sets configurations as active, individually. For each configuration, use gsutil compute instances list to get a list of compute resources.
	- C. Go to Cloud Shell and export this information to Cloud Storage on a daily basis.
	- D. Go to GCP Console and export this information to Cloud SQL on a daily basis.
	
	- **A**. To list all compute engine instances, the command is `gcloud compute instances list` command. This command run within a project. Since there is two projects, we need to create two configuration with individual Project ID. Because we want automatic process, we can write a script to execute daily
	
	
85. You have a large 5-TB AVRO file stored in a Cloud Storage bucket. Your analysts are proficient only in SQL and need access to the data stored in this file. You want to find a cost-effective way to complete their request as soon as possible. What should you do?
	- A. Load data in Cloud Datastore and run a SQL query against it.
	- B. Create a BigQuery table and load data in BigQuery. Run a SQL query on this table and drop this table after you complete your request.
	- C. Create external tables in BigQuery that point to Cloud Storage buckets and run a SQL query on these external tables to complete your request.
	- D. Create a Hadoop cluster and copy the AVRO file to NDFS by compressing it. Load the file in a hive table and provide access to your analysts so that they can run SQL queries.
	
	- **C**. The best options for Analysis with SQL is to use BigQuery. It support SQL syntax and good for analysis. Since the data is already exist in Cloud Storage, there is no need to load data again in BigQuery for extra cost. You can create external tables in BigQuery pointing to Cloud Storage buckets for analysis
	
86. You need to verify that a Google Cloud Platform service account was created at a particular time. What should you do?
	- A. Filter the Activity log to view the Configuration category. Filter the Resource type to Service Account.
	- B. Filter the Activity log to view the Configuration category. Filter the Resource type to Google Project.
	- C. Filter the Activity log to view the Data Access category. Filter the Resource type to Service Account.
	- D. Filter the Activity log to view the Data Access category. Filter the Resource type to Google Project.
	
	- **A**. We looks for service account so filter should be set to service account. We want to know the details about service account itself, not what service account has done. So we go for Configuration category


87. You deployed an LDAP server on Compute Engine that is reachable via TLS through port 636 using UDP. You want to make sure it is reachable by clients over that port. What should you do?
	- A. Add the network tag allow-udp-636 to the VM instance running the LDAP server.
	- B. Create a route called allow-udp-636 and set the next hop to be the VM instance running the LDAP server.
	- C. Add a network tag of your choice to the instance. Create a firewall rule to allow ingress on UDP port 636 for that network tag.
	- D. Add a network tag of your choice to the instance running the LDAP server. Create a firewall rule to allow egress on UDP port 636 for that network tag.
	
	- **C**. To make sure that the LDAP server is reachable by clients over port 636 using UDP, you need to allow ingress traffic on that port. Ingress means request going into that resource. To achieve, you can crdaete a network tag and specify UDP port 636. The name of network tag is up to you
	
88. You need to set a budget alert for use of Compute Engineer services on one of the three Google Cloud Platform projects that you manage. All three projects are linked to a single billing account. What should you do?
	- A. Verify that you are the project billing administrator. Select the associated billing account and create a budget and alert for the appropriate project.
	- B. Verify that you are the project billing administrator. Select the associated billing account and create a budget and a custom alert.
	- C. Verify that you are the project administrator. Select the associated billing account and create a budget for the appropriate project.
	- D. Verify that you are project administrator. Select the associated billing account and create a budget and a custom alert.
	
	- **A**. To set budget and alert, you need to be Billing Administrator. Porject admin do not have permission on budget. Then we can rely on the default budget and alert behavior to create budget and alert for the individual project interested.

89. You are migrating a production-critical on-premises application that requires 96 vCPUs to perform its task. You want to make sure the application runs in a similar environment on GCP. What should you do?
	- A. When creating the VM, use machine type n1-standard-96.
	- B. When creating the VM, use Intel Skylake as the CPU platform.
	- C. Create the VM using Compute Engine default settings. Use gcloud to modify the running instance to have 96 vCPUs.
	- D. Start the VM using Compute Engine default settings, and adjust as you go based on Rightsizing Recommendations.
	
	- **A**. Obviously enough, *n1-standard-96* fit best as it support 96 vCPU which is the same as on-premise application. Note that you can change the machine type after you create them but you have to stop VM. so C is not correct. 
	
90. You want to configure a solution for archiving data in a Cloud Storage bucket. The solution must be cost-effective. Data with multiple versions should be archived after 30 days. Previous versions are accessed once a month for reporting. This archive data is also occasionally updated at month-end. What should you do?
	- A. Add a bucket lifecycle rule that archives data with newer versions after 30 days to Coldline Storage.
	- B. Add a bucket lifecycle rule that archives data with newer versions after 30 days to Nearline Storage.
	- C. Add a bucket lifecycle rule that archives data from regional storage after 30 days to Coldline Storage.
	- D. Add a bucket lifecycle rule that archives data from regional storage after 30 days to Nearline Storage
	
	- **B**. Only data with multiple version should be archived. We set the storage class change life cycle for data with newer version to 30 days. Since data is roughly access once a month, Nearline storage fit this need. 
	
91. Your company's infrastructure is on-premises, but all machines are running at maximum capacity. You want to burst to Google Cloud. The workloads on Google
Cloud must be able to directly communicate to the workloads on-premises using a private IP range. What should you do?
	- A. In Google Cloud, configure the VPC as a host for Shared VPC.
	- B. In Google Cloud, configure the VPC for VPC Network Peering.
	- C. Create bastion hosts both in your on-premises environment and on Google Cloud. Configure both as proxy servers using their public IP addresses.
	- D. Set up Cloud VPN between the infrastructure on-premises and Google Cloud.
	
	- **D**. Cloud VPN or Interconnect allows you to communicate on-premise with Google Cloud using private IP. Cloud Peering is for VPC to VPC
	
92. You want to select and configure a solution for storing and archiving data on Google Cloud Platform. You need to support compliance objectives for data from one geographic location. This data is archived after 30 days and needs to be accessed annually. What should you do?
	- A. Select Multi-Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Coldline Storage.
	- B. Select Multi-Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Nearline Storage.
	- C. Select Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Nearline Storage.
	- D. Select Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Coldline Storage.
	
	- **D**. The data only need to be stored in one geographic location therefore a Regional Storage is sufficient. Archived is done after 30 days so add a bucket lifecycle rule of storage class change after 30days. Access is annually, the coldline storage is good for anything >90days but less or equal to 1 year
	
93. Your company uses BigQuery for data warehousing. Over time, many different business units in your company have created 1000+ datasets across hundreds of projects. Your CIO wants you to examine all datasets to find tables that contain an employee_ssn column. You want to minimize effort in performing this task.
What should you do?
	- A. Go to Data Catalog and search for employee_ssn in the search box.
	- B. Write a shell script that uses the bq command line tool to loop through all the projects in your organization.
	- C. Write a script that loops through all the projects in your organization and runs a query on INFORMATION_SCHEMA.COLUMNS view to find the employee_ssn column.
	- D. Write a Cloud Dataflow job that loops through all the projects in your organization and runs a query on INFORMATION_SCHEMA.COLUMNS view to find employee_ssn column.
	
	- **A**. For easy and quick solution, we want to avoid writing any scripts. Data Catalog provide meta data management services allowing search functionaility to datasets, tables, columns and other meta data
	
94. You create a Deployment with 2 replicas in a Google Kubernetes Engine cluster that has a single preemptible node pool. After a few minutes, you use kubectl to examine the status of your Pod and observe that one of them is still in Pending status (Age of 9m) : What is the most likely cause?
	- A. The pending Pod's resource requests are too large to fit on a single node of the cluster.
	- B. Too many Pods are already running in the cluster, and there are not enough resources left to schedule the pending Pod.
	- C. The node pool is configured with a service account that does not have permission to pull the container image used by the pending Pod.
	- D. The pending Pod was originally scheduled on a node that has been preempted between the creation of the Deployment and your verification of the Pods' status. It is currently being rescheduled on a new node.
	
	- **D or B**. I am leaning toward D from exam perspective. As the question mention **single preemptible node pool**. It can happen if the pod was schedule on one pod and preempted. Kubernetes will re-position the Pod to a different node, causing the previous node to be in pending. However, B is also reasonable because lack of resource is one very common reason for pending status. However, consider we have only 2 replicas, and the question mention "preemptible node pool", I'll go with **D**.

95. You want to find out when users were added to Cloud Spanner Identity Access Management (IAM) roles on your Google Cloud Platform (GCP) project. What should you do in the GCP Console?
	- A. Open the Cloud Spanner console to review configurations.
	- B. Open the IAM & admin console to review IAM policies for Cloud Spanner roles.
	- C. Go to the Stackdriver Monitoring console and review information for Cloud Spanner.
	- D. Go to the Stackdriver Logging console, review admin activity logs, and filter them for Cloud Spanner IAM roles.
	
	- **D**. Find out *When* users were added is a history event, falls under Auditing category. When viewing auditing stuff, go to Logging console. This belongs to admin activity logs with Cloud Spanner IAM category. 
	
96. Your company implemented BigQuery as an enterprise data warehouse. Users from multiple business units run queries on this data warehouse. However, you notice that query costs for BigQuery are very high, and you need to control costs. Which two methods should you use? (Choose two.)
	- A. Split the users from business units to multiple projects.
	- B. Apply a user- or project-level custom query quota for BigQuery data warehouse.
	- C. Create separate copies of your BigQuery data warehouse for each business unit.
	- D. Split your BigQuery data warehouse into multiple data warehouses for each business unit.
	- E. Change your BigQuery query model from on-demand to flat rate. Apply the appropriate number of slots to each Project.
	
	- **B and E**. Setting a custom query quote will limit the amount of data that can be queryed within a certain amount of time, which controll the cost. You Might also change from `on-demand` to `flat rate` model for better cost controll should your team query a lot to the extent where on-demand does not make sense. Other options do not change the price/query nor amount of query run, therefore do not help in managing cost
	
97. You are building a product on top of Google Kubernetes Engine (GKE). You have a single GKE cluster. For each of your customers, a Pod is running in that cluster, and your customers can run arbitrary code inside their Pod. You want to maximize the isolation between your customers' Pods. What should you do?
	- A. Use Binary Authorization and whitelist only the container images used by your customers' Pods.
	- B. Use the Container Analysis API to detect vulnerabilities in the containers used by your customers' Pods.
	- C. Create a GKE node pool with a sandbox type configured to gvisor. Add the parameter runtimeClassName: gvisor to the specification of your customers' Pods.
	- D. Use the cos_containerd image for your GKE nodes. Add a nodeSelector with the value cloud.google.com/gke-os-distribution: cos_containerd to the specification of your customers' Pods
	
	- **C**. If looking for isolation of pods in GKE, user can leverage the Node Pool **Sandbox** type, which is run by gVisor. https://cloud.google.com/kubernetes-engine/docs/concepts/sandbox-pods
	
98. Your customer has implemented a solution that uses Cloud Spanner and notices some read latency-related performance issues on one table. This table is accessed only by their users using a primary key. The table schema is shown below.

	```SQL
	CREATE TABLE Persons (
		person_id INT64 NOT NULL,
		account_creation_date DATE,
		birthdate DATE,
		firstname STRING(255),
		lastname STRING(255),
		profile_picture BYTES(255)
	) PRIMARY_KEY (person_id)
	```

	- A. Remove the profile_picture field from the table.
	- B. Add a secondary index on the person_id column.
	- C. Change the primary key to not have monotonically increasing values.
	- D. Create a secondary index using the following Data Definition Language (DDL): 
		
		```SQL
		CREATE INDEX person_id_ix ON Persons (
			person_id, 
			firstname,
			lastname
		) STORING (profile_picture)
		```
		
	- **C**. The data is only accessed through primary key, which already indexed. Adding other index will not help. You cannot remove a field as well. So "Change the primary key to not have monotonically increasing values" works because Cloud Spanner divides data among servers by key ranges. Having incremental PK will result in inserts always happening in a single server. https://cloud.google.com/spanner/docs/schema-design#primary-key-prevent-hotspots

99. Your finance team wants to view the billing report for your projects. You want to make sure that the finance team does not get additional permissions to the project. What should you do?
	- A. Add the group for the finance team to roles/billing user role.
	- B. Add the group for the finance team to roles/billing admin role.
	- C. Add the group for the finance team to roles/billing viewer role.
	- D. Add the group for the finance team to roles/billing project/Manager role.
	
	- **C**. Billing Account Viewer access would usually be granted to finance teams, it provides access to spend information, but does not confer the right to link or unlink projects or otherwise manage the properties of the billing account. https://cloud.google.com/billing/docs/how-to/billing-access. 
	
100. Your organization has strict requirements to control access to Google Cloud projects. You need to enable your Site Reliability Engineers (SREs) to approve requests from the Google Cloud support team when an SRE opens a support case. You want to follow Google-recommended practices. What should you do?
     - A. Add your SREs to roles/iam.roleAdmin role.
     - B. Add your SREs to roles/accessapproval.approver role.
     - C. Add your SREs to a group and then add this group to roles/iam.roleAdmin.role.
     - D. Add your SREs to a group and then add this group to roles/accessapproval.approver role.

     - **D**. Always add user to group and add group to roles or give group permission. Here specify strict requirements and the use case is to Approve request but nothing else. So `accessapproval.approver` is better than more generic `iam.roleAdmin`. 
	
	
101. You need to host an application on a Compute Engine instance in a project shared with other teams. You want to prevent the other teams from accidentally causing downtime on that application. Which feature should you use?
	 - A. Use a Shielded VM.
	 - B. Use a Preemptible VM.
	 - C. Use a sole-tenant node.
	 - D. Enable deletion protection on the instance.
	
	 - **D (Likely)**. Delete protection will prevent accidental delete of instance. This can help prevently other teams to delete it. It is definitely a feature to accidentally causing downtime, even through it does not cover all scenarios (https://cloud.google.com/compute/docs/instances/preventing-accidental-vm-deletion). Sole-tenant however, is talking about dedicate physical compute engine server. It is about hardware isolation and usually for performance and security purpose. It does not prevent human error.


102. Your organization needs to grant users access to query datasets in BigQuery but prevent them from accidentally deleting the datasets. You want a solution that follows Google-recommended practices. What should you do?
	 - A. Add users to roles/bigquery user role only, instead of roles/bigquery dataOwner.
	 - B. Add users to roles/bigquery dataEditor role only, instead of roles/bigquery dataOwner.
	 - C. Create a custom role by removing delete permissions, and add users to that role only.
	 - D. Create a custom role by removing delete permissions. Add users to the group, and then add the group to the custom role.
	
	 - **D**. BigQuery Data User do not have ability to create and update data. Based on what it says, it should only remove deleting ability. There is no predefined role for this type. So need custom role. Follow best practice, you add user to group, assign group to role. so D is correct

103. You have a developer laptop with the Cloud SDK installed on Ubuntu. The Cloud SDK was installed from the Google Cloud Ubuntu package repository. You want to test your application locally on your laptop with Cloud Datastore. What should you do?
	 - A. Export Cloud Datastore data using gcloud datastore export.
	 - B. Create a Cloud Datastore index using gcloud datastore indexes create.
	 - C. Install the google-cloud-sdk-datastore-emulator component using the apt get install command.
	 - D. Install the cloud-datastore-emulator component using the gcloud components install command.
	
	 - **C**. Use Datastore emulator to develop and test application locally. https://cloud.google.com/datastore/docs/tools/datastore-emulator. Normally, you would install it with `gcloud components install cloud-datastore-emulator`. But this specific case because you install cloud SDK in Ubuntu, you need to install through `apt-get`. https://cloud.google.com/sdk/docs/install#deb. Otherwise you see error: You cannot perform this action because the Cloud SDK component manager is disabled for this installation

104. Your company set up a complex organizational structure on Google Cloud. The structure includes hundreds of folders and projects. Only a few team members should be able to view the hierarchical structure. You need to assign minimum permissions to these team members, and you want to follow Google-recommended practices. What should you do?
     - A. Add the users to roles/browser role.
     - B. Add the users to roles/iam.roleViewer role.
     - C. Add the users to a group, and add this group to roles/browser.
     - D. Add the users to a group, and add this group to roles/iam.roleViewer role.
 
     - **C**. Again, add user to group and add group to role. Here we focus on hierarchical structure (project, folders, etc) not user permission. So `roles/broswer` is the answer.
	
105. Your company has a single sign-on (SSO) identity provider that supports Security Assertion Markup Language (SAML) integration with service providers. Your company has users in Cloud Identity. You would like users to authenticate using your company's SSO provider. What should you do?
	 - A. In Cloud Identity, set up SSO with Google as an identity provider to access custom SAML apps.
     - B. In Cloud Identity, set up SSO with a third-party identity provider with Google as a service provider.
	 - C. Obtain OAuth 2.0 credentials, configure the user consent screen, and set up OAuth 2.0 for Mobile & Desktop Apps.
	 - D. Obtain OAuth 2.0 credentials, configure the user consent screen, and set up OAuth 2.0 for Web Server Applications.
	
	 - **B**. First of all, SAML and OAuth are completely different. OAuth handles authorization only. In SAML Based SSO, user sign in with partner using Email and password, and hand saml reponse to Google for access service. Google act as Service Provider, partner act as Identity Provider. https://support.google.com/cloudidentity/answer/6262987?hl=en&ref_topic=7558767
	
106. Your organization has a dedicated person who creates and manages all service accounts for Google Cloud projects. You need to assign this person the minimum role for projects. What should you do?
	 - A. Add the user to roles/iam.roleAdmin role.
	 - B. Add the user to roles/iam.securityAdmin role.
	 - C. Add the user to roles/iam.serviceAccountUser role.
	 - D. Add the user to roles/iam.serviceAccountAdmin role.
	
	 - **D**. With least priviledge, here we talk about service account so no need to worry about other permission. With service account user, one can list, get detials and impersonate service account. In order to create and manage service account, you need to have `serviceAccountAdmin` Role
	
107. You are building an archival solution for your data warehouse and have selected Cloud Storage to archive your data. Your users need to be able to access this archived data once a quarter for some regulatory requirements. You want to select a cost-efficient option. Which storage option should you use?
	 - A. Cold Storage
	 - B. Nearline Storage
	 - C. Regional Storage
	 - D. Multi-Regional Storage
	
	 - **B**. Not a great question. As the correct storage option name should be "Coldline" storage. On the side, accessing once a quarter is at the margin of 90 days which is the minimun storage duration for coldline storage. I'd go nearline to play safe

108. A team of data scientists infrequently needs to use a Google Kubernetes Engine (GKE) cluster that you manage. They require GPUs for some long-running, non- restartable jobs. You want to minimize cost. What should you do?
	 - A. Enable node auto-provisioning on the GKE cluster.
	 - B. Create a VerticalPodAutscaler for those workloads.
	 - C. Create a node pool with preemptible VMs and GPUs attached to those VMs.
	 - D. Create a node pool of instances with GPUs, and enable autoscaling on this node pool with a minimum size of 1.
	
	 - **A**. D works for most part except for "infrequently". With option D you keep node running all the time which is no necessary. with A, node pool is created and deleted automatically based on workload. Auto-provisioning enable auto scaling as well, which you can specify min number of instance. so A include D, but more than D. https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-provisioning

109. Your organization has user identities in Active Directory. Your organization wants to use Active Directory as their source of truth for identities. Your organization wants to have full control over the Google accounts used by employees for all Google services, including your Google Cloud Platform (GCP) organization. What should you do?
	 - A. Use Google Cloud Directory Sync (GCDS) to synchronize users into Cloud Identity.
	 - B. Use the cloud Identity APIs and write a script to synchronize users to Cloud Identity.
	 - C. Export users from Active Directory as a CSV and import them to Cloud Identity via the Admin Console.
	 - D. Ask each employee to create a Google account using self signup. Require that each employee use their company email address and password.

	 - **A**. When work with identity in Active Directory, use Google Cloud Directory Sync (GCDS) for identity. This is one-way sync which means change in GCP do not go back to Active Directory
	
110. You have successfully created a development environment in a project for an application. This application uses Compute Engine and Cloud SQL. Now you need to create a production environment for this application. The security team has forbidden the existence of network routes between these 2 environments and has asked you to follow Google-recommended practices. What should you do?
	 - A. Create a new project, enable the Compute Engine and Cloud SQL APIs in that project, and replicate the setup you have created in the development environment.
	 - B. Create a new production subnet in the existing VPC and a new production Cloud SQL instance in your existing project, and deploy your application using those resources.
	 - C. Create a new project, modify your existing VPC to be a Shared VPC, share that VPC with your new project, and replicate the setup you have in the development environment in that new project in the Shared VPC.
	 - D. Ask the security team to grant you the Project Editor role in an existing production project used by another division of your company. Once they grant you that role, replicate the setup you have in the development environment in that project.
	
	 - **A**. This will create a new VPC and other resources for production. Since it is a different VPC, there will be no communication between prod and dev. B and C are both incorrect as subnet in VPC, as well as Shared VPC allow two resources to communicate privately. D is no need, it doesn't make sense to jump into other team's project for your setup
	
111. Your management has asked an external auditor to review all the resources in a specific project. The security team has enabled the Organization Policy called
Domain Restricted Sharing on the organization node by specifying only your Cloud Identity domain. You want the auditor to only be able to view, but not modify, the resources in that project. What should you do?
	 - A. Ask the auditor for their Google account, and give them the Viewer role on the project.
	 - B. Ask the auditor for their Google account, and give them the Security Reviewer role on the project.
	 - C. Create a temporary account for the auditor in Cloud Identity, and give that account the Viewer role on the project.
	 - D. Create a temporary account for the auditor in Cloud Identity, and give that account the Security Reviewer role on the project.
	
	 - **C**. Auditor is granted with "Viewer" role to view all resources in the project. "Secutiry Reviewer" role only allow you to review security policy but not acutal project info. https://cloud.google.com/iam/docs/job-functions/auditing#scenario_external_auditors. The Organizarion has Domain Restricted Sharing to only your domain. This means that any Google Account outside of your domain cannot be use in Cloud Identity. so go for C


112. You have a workload running on Compute Engine that is critical to your business. You want to ensure that the data on the boot disk of this workload is backed up regularly. You need to be able to restore a backup as quickly as possible in case of disaster. You also want older backups to be cleaned automatically to save on cost. You want to follow Google-recommended practices. What should you do?
	 - A. Create a Cloud Function to create an instance template.
	 - B. Create a snapshot schedule for the disk using the desired interval.
	 - C. Create a cron job to create a new disk from the disk using gcloud.
	 - D. Create a Cloud Task to create an image and export it to Cloud Storage.
	
	 - **B**. To backup persistent disk, it is recommended to use snapshot. It is an independent object and detached from disk. You can delete the disk and snapshot will stay, or create disk from snapshot and mount to another VM. You can also configure autodelete on snapshot. https://cloud.google.com/compute/docs/disks/scheduled-snapshots
	
113. You need to assign a Cloud Identity and Access Management (Cloud IAM) role to an external auditor. The auditor needs to have permissions to review your
Google Cloud Platform (GCP) Audit Logs and also to review your Data Access logs. What should you do?
	 - A. Assign the auditor the IAM role roles/logging.privateLogViewer. Perform the export of logs to Cloud Storage.
	 - B. Assign the auditor the IAM role roles/logging.privateLogViewer. Direct the auditor to also review the logs for changes to Cloud IAM policy.
	 - C. Assign the auditor's IAM user to a custom role that has logging.privateLogEntries.list permission. Perform the export of logs to Cloud Storage.
	 - D. Assign the auditor's IAM user to a custom role that has logging.privateLogEntries.list permission. Direct the auditor to also review the logs for changes to Cloud IAM policy.
	
	 - **B**. There are two buckets of logs. `_Required` bucket stored Admin Activity and System Event Log. The `_Default` bucket store Data Access log and Policy Defined Log. In order to view all for these two bucket, you need *Private Logs Viewer` role. (Logs Viewer role do not give permission to Data Access Log ). https://cloud.google.com/logging/docs/access-control#considerations. We are viewing directly in Cloud logging bucket with these permission so no need to export to Cloud Storage. (That would be Cloud Storage object viewer role instead). 

114. You are managing several Google Cloud Platform (GCP) projects and need access to all logs for the past 60 days. You want to be able to explore and quickly analyze the log contents. You want to follow Google-recommended practices to obtain the combined logs for all projects. What should you do?
	 - A. Navigate to Stackdriver Logging and select resource.labels.project_id="*"
	 - B. Create a Stackdriver Logging Export with a Sink destination to a BigQuery dataset. Configure the table expiration to 60 days.
	 - C. Create a Stackdriver Logging Export with a Sink destination to Cloud Storage. Create a lifecycle rule to delete objects after 60 days.
	 - D. Configure a Cloud Scheduler job to read from Stackdriver and store the logs in BigQuery. Configure the table expiration to 60 days.
	
	 - **B**. One can choose logging sink designation. When talking about quickly analyze, bigQuery is usually the go to answer. You do not need to have job, cloud logging provide logging export natively. When compare log store in cloud logging bucket vs Cloud storage, Cloud Logging is better in query and monitoring/alerting, where as cloud storage is better at file management
	
115. You need to reduce GCP service costs for a division of your company using the fewest possible steps. You need to turn off all configured services in an existing
GCP project. What should you do?
     -  A. 1. Verify that you are assigned the Project Owners IAM role for this project. 2. Locate the project in the GCP console, click Shut down and then enter the project ID.
	 - B. 1. Verify that you are assigned the Project Owners IAM role for this project. 2. Switch to the project in the GCP console, locate the resources and delete them.
	 - C. 1. Verify that you are assigned the Organizational Administrator IAM role for this project. 2. Locate the project in the GCP console, enter the project ID and then click Shut down.
	 - D. 1. Verify that you are assigned the Organizational Administrators IAM role for this project. 2. Switch to the project in the GCP console, locate the resources and delete them.
	
	 - **A**. This is talking about GCP project, not anything at organizational level. So we need Project related roles that is able to shut down project. Project owner is the one. It says turn off all services, not deleting them. 
	
116. You are configuring service accounts for an application that spans multiple projects. Virtual machines (VMs) running in the web-applications project need access to BigQuery datasets in crm-databases-proj. You want to follow Google-recommended practices to give access to the service account in the web-applications project. What should you do?
	 - A. Give `project owner` for web-applications appropriate roles to crm-databases-proj.
	 - B. Give `project owner` role to crm-databases-proj and the web-applications project.
	 - C. Give `project owner` role to crm-databases-proj and bigquery.dataViewer role to web-applications.
	 - D. Give `bigquery.dataViewer` role to crm-databases-proj and appropriate roles to web-applications.
	
	 - **D**. Remember, you always grant permission in destination. So BigQuery is in `crm-databases-proj`, grant bigquery.dataViewer role in crm-database-proj. Then give whatever role need in web-application project

117. An employee was terminated, but their access to Google Cloud was not removed until 2 weeks later. You need to find out if this employee accessed any sensitive customer information after their termination. What should you do?
		- A. View System Event Logs in Cloud Logging. Search for the user's email as the principal.
		- B. View System Event Logs in Cloud Logging. Search for the service account associated with the user.
		- C. View Data Access audit logs in Cloud Logging. Search for the user's email as the principal.
		- D. View the Admin Activity log in Cloud Logging. Search for the service account associated with the user.
	
		- **C**. Data Access Log record all activity related to accessing and modifying data. This is perfect for track	ing user data access in this scenarios
	
118. You need to create a custom IAM role for use with a GCP service. All permissions in the role must be suitable for **production use**. You also want to clearly share with your organization the status of the custom role. This will be the **first version** of the custom role. What should you do?
	 - A. Use permissions in your role that use the 'supported' support level for role permissions. Set the role stage to ALPHA while testing the role permissions.
	 - B. Use permissions in your role that use the 'supported' support level for role permissions. Set the role stage to BETA while testing the role permissions.
	 - C. Use permissions in your role that use the 'testing' support level for role permissions. Set the role stage to ALPHA while testing the role permissions.
	 - D. Use permissions in your role that use the 'testing' support level for role permissions. Set the role stage to BETA while testing the role permissions.
	
	 - **A**. For role that eventually need to be used in production, we want to use permission with "supported" support level. https://cloud.google.com/iam/docs/custom-roles-permissions-support. As for the first version, it will be "ALPHA" and only expose to a small user group.

119. Your company has a large quantity of unstructured data in different file formats. You want to perform ETL transformations on the data. You need to make the data accessible on Google Cloud so it can be processed by a Dataflow job. What should you do?
	 - A. Upload the data to BigQuery using the bq command line tool.
	 - B. Upload the data to Cloud Storage using the gsutil command line tool.
	 - C. Upload the data into Cloud SQL using the import function in the console.
	 - D. Upload the data into Cloud Spanner using the import function in the console.
	
	 - **B**. For unstructed Data, especially with different file formats, use Cloud Storage. Cloud storage store unstructed objects, which can be files. 


120. You need to manage multiple Google Cloud projects in the fewest steps possible. You want to configure the Google Cloud SDK command line interface (CLI) so that you can easily manage multiple projects. What should you do?
		- A. 1. Create a configuration for each project you need to manage. 2. Activate the appropriate configuration when you work with each of your assigned Google Cloud projects.
		- B. 1. Create a configuration for each project you need to manage. 2. Use gcloud init to update the configuration values when you need to work with a non-default project
		- C. 1. Use the default configuration for one project you need to manage. 2. Activate the appropriate configuration when you work with each of your assigned Google Cloud projects.
		- D. 1. Use the default configuration for one project you need to manage. 2. Use gcloud init to update the configuration values when you need to work with a non-default project.
		
		- **A**. To manage multiple projects, you need to have individual configuration for each project. And to use a particular configuration to manage that project, you need to activate the configuration. You can use gcloud command. `gcloud config configurations create <config_id>` to create, and `gcloud config configurations activate`
	
121. Your managed instance group raised an alert stating that new instance creation has failed to create new instances. You need to maintain the number of running instances specified by the template to be able to process expected application traffic. What should you do?
	 - A. Create an instance template that contains valid syntax which will be used by the instance group. Delete any persistent disks with the same name as instance names.
	 - B. Create an instance template that contains valid syntax that will be used by the instance group. Verify that the instance name and persistent disk name values are not the same in the template.
	 - C. Verify that the instance template being used by the instance group contains valid syntax. Delete any persistent disks with the same name as instance names. Set the disks.autoDelete property to true in the instance template.
	 - D. Delete the current instance template and replace it with a new instance template. Verify that the instance name and persistent disk name values are not the same in the template. Set the disks.autoDelete property to true in the instance template.
	
	 - **A**. There are 3 main reasons that MIG cannot create instances. 1. Syntax Error 2. Boot disk exist 3. Limit exceed. A cover the troubleshooting for both syntax error and disk name issue. (When creating instance, the persistant disk name shall be the same as instance name, which should not exist). https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-migs
	
	
122. Your company is moving from an on-premises environment to Google Cloud. You have multiple development teams that use Cassandra environments as backend databases. They all need a development environment that is isolated from other Cassandra instances. You want to move to Google Cloud **quickly and with minimal support** effort. What should you do?
	 - A. 1. Build an instruction guide to install Cassandra on Google Cloud. 2. Make the instruction guide accessible to your developers.
	 - B. 1. Advise your developers to go to Cloud Marketplace. 2. Ask the developers to launch a Cassandra image for their development work.
	 - C. 1. Build a Cassandra Compute Engine instance and take a snapshot of it. 2. Use the snapshot to create instances for your developers.
	 - D. 1. Build a Cassandra Compute Engine instance and take a snapshot of it. 2. Upload the snapshot to Cloud Storage and make it accessible to your developers. 3. Build instructions to create a Compute Engine instance from the snapshot so that developers can do it themselves.
	
	 - **B**. They keyword is quickly with miminal support. So we want managed, ready-to-use service, go to Google Market Place. Also there is no mention for customization so Market Place will fit. No need to manual configure anything.


123. You have a Compute Engine instance hosting a production application. You want to receive an email if the instance consumes more than 90% of its CPU resources for more than 15 minutes. You want to use Google services. What should you do?
	 - A. 1. Create a consumer Gmail account. 2. Write a script that monitors the CPU usage. 3. When the CPU usage exceeds the threshold, have that script send an email using the Gmail account and smtp.gmail.com on port 25 as SMTP server.
	 - B. 1. Create a Cloud Monitoring Workspace and associate your Google Cloud Platform (GCP) project with it. 2. Create a Cloud Monitoring Alerting Policy that uses the threshold as a trigger condition. 3. Configure your email address in the notification channel.
	 - C. 1. Create a Cloud Monitoring Workspace and associate your GCP project with it. 2. Write a script that monitors the CPU usage and sends it as a custom metric to Cloud Monitoring. 3. Create an uptime check for the instance in Cloud Monitoring.
	 - D. 1. In Cloud Logging, create a logs-based metric to extract the CPU usage by using this regular expression: CPU Usage: ([0-9] {1,3})% 2. In Cloud Monitoring, create an Alerting Policy based on this metric. 3. Configure your email address in the notification channel.

	 - **B**. This is about cloud monitoring and alerting because >90% CPU is a mertic. Mertic is for monitoring. You can use Cloud Monitoring alerting policy to notification to certain email. Trigger is threshold (>90%)
	
124. You have an application that uses Cloud Spanner as a backend database. The application has a very predictable traffic pattern. You want to automatically scale up or down the number of Spanner nodes depending on traffic. What should you do?
	 - A. Create a cron job that runs on a scheduled basis to review Cloud Monitoring metrics, and then resize the Spanner instance accordingly.
	 - B. Create a Cloud Monitoring alerting policy to send an alert to oncall SRE emails when Cloud Spanner CPU exceeds the threshold. SREs would scale resources up or down accordingly.
	 - C. Create a Cloud Monitoring alerting policy to send an alert to Google Cloud Support email when Cloud Spanner CPU exceeds your threshold. Google support would scale resources up or down accordingly.
	 - D. Create a Cloud Monitoring alerting policy to send an alert to webhook when Cloud Spanner CPU is over or under your threshold. Create a Cloud Function that listens to HTTP and resizes Spanner resources accordingly.
	
	 - **D**. The automation is the key to auto scalling. The cron job based on schedule is lack of flexibility and cannot handle unexpected traffic change very well. Also it did not leverage the google service. Instead, we take advantage of Cloud Monitoring, and build a cloud function to scalling based on monitoring threshold.
	
125. Your company publishes large files on an Apache web server that runs on a Compute Engine instance. The Apache web server is not the only application running in the project. You want to receive an email when the egress network costs for the server exceed 100 dollars for the current month as measured by Google Cloud.
What should you do?
	 - A. Set up a budget alert on the project with an amount of 100 dollars, a threshold of 100%, and notification type of ג€email.ג€
	 - B. Set up a budget alert on the billing account with an amount of 100 dollars, a threshold of 100%, and notification type of ג€email.ג€
	 - C. Export the billing data to BigQuery. Create a Cloud Function that uses BigQuery to sum the egress network costs of the exported billing data for the Apache web server for the current month and sends an email if it is over 100 dollars. Schedule the Cloud Function using Cloud Scheduler to run hourly.
	 - D. Use the Cloud Logging Agent to export the Apache web server logs to Cloud Logging. Create a Cloud Function that uses BigQuery to parse the HTTP response log data in Cloud Logging for the current month and sends an email if the size of all HTTP responses, multiplied by current Google Cloud egress prices, totals over 100 dollars. Schedule the Cloud Function using Cloud Scheduler to run hourly.
	
	 - **C**. Billing data can be exported to Bigquery for analysis. Use light weight cloud function to calculated egress network cost by Apache server and send email is the easiest step. *D* is more complicated
	
126. You have designed a solution on Google Cloud that uses multiple Google Cloud products. Your company has asked you to estimate the costs of the solution. You need to provide estimates for the monthly total cost. What should you do?
	 - A. For each Google Cloud product in the solution, review the pricing details on the products pricing page. Use the pricing calculator to total the monthly costs for each Google Cloud product.
	 - B. For each Google Cloud product in the solution, review the pricing details on the products pricing page. Create a Google Sheet that summarizes the expected monthly costs for each product.
	 - C. Provision the solution on Google Cloud. Leave the solution provisioned for 1 week. Navigate to the Billing Report page in the Cloud Console. Multiply the 1 week cost to determine the monthly costs.
	 - D. Provision the solution on Google Cloud. Leave the solution provisioned for 1 week. Use Cloud Monitoring to determine the provisioned and used resource amounts. Multiply the 1 week cost to determine the monthly costs.
	
	 - **A**. Google provide pricing calculator to estimating the cost. No need to calculate yourself or provisioning for a weel. 
	 
127. You have an application that receives SSL-encrypted TCP traffic on port 443. Clients for this application are located all over the world. You want to minimize latency for the clients. Which load balancing option should you use?
	 - A. HTTPS Load Balancer
	 - B. Network Load Balancer
	 - C. SSL Proxy Load Balancer
	 - D. Internal TCP/UDP Load Balancer. Add a firewall rule allowing ingress traffic from 0.0.0.0/0 on the target instances.
	
	 - **C**. Let's keep load balancing concept simple. For HTTPS traffic use HTTPS load balancer. For non-HTTP traffic, use SSL Proxy Load Balancer(SSL, TCP). (https://cloud.google.com/load-balancing/docs/ssl). Network Load Balancer (Extenral TCP/UDP network load balancer) for regional pass through traffic (https://cloud.google.com/load-balancing/docs/network). Here it mentioned SSL-encrypted TCP traffic all over the world, go for SSL proxy load balancer. 

128. You have an application on a general-purpose Compute Engine instance that is experiencing excessive disk read throttling on its Zonal SSD Persistent Disk. The application primarily reads large files from disk. The disk size is currently 350 GB. You want to provide the maximum amount of throughput while minimizing costs.
What should you do?
	 - A. Increase the size of the disk to 1 TB.
	 - B. Increase the allocated CPU to the instance.
	 - C. Migrate to use a Local SSD on the instance.
	 - D. Migrate to use a Regional SSD on the instance.
	
	 - **C**. One advantage of Local SSD over persistent disk it is high Input Out Speed per second IOPS and low latency. 

129. Your Dataproc cluster runs in a single Virtual Private Cloud (VPC) network in a single subnet with range 172.16.20.128/25. There are no private IP addresses available in the VPC network. You want to add new VMs to communicate with your cluster using the minimum number of steps. What should you do?
	 - A. Modify the existing subnet range to 172.16.20.0/24.
	 - B. Create a new Secondary IP Range in the VPC and configure the VMs to use that range.
	 - C. Create a new VPC network for the VMs. Enable VPC Peering between the VMs' VPC network and the Dataproc cluster VPC network.
	 - D. Create a new VPC network for the VMs with a subnet of 172.32.0.0/16. Enable VPC network Peering between the Dataproc VPC network and the VMs VPC network. Configure a custom Route exchange.
	
	 - **C**. Straight forward. There is no private IP address available in the VPC so you cannot expand IP range to obtain new availability. You need to create a new VPC. Enable VPC peering will allow new VM to communicate with existing Dataproc cluster

130. You manage an App Engine Service that aggregates and visualizes data from BigQuery. The application is deployed with the default App Engine Service account.
The data that needs to be visualized resides in a different project managed by another team. You do not have access to this project, but you want your application to be able to read data from the BigQuery dataset. What should you do?
	 - A. Ask the other team to grant your default App Engine Service account the role of BigQuery Job User.
	 - B. Ask the other team to grant your default App Engine Service account the role of BigQuery Data Viewer.
	 - C. In Cloud IAM of your project, ensure that the default App Engine service account has the role of BigQuery Data Viewer.
	 - D. In Cloud IAM of your project, grant a newly created service account from the other team the role of BigQuery Job User in your project.
	
	 - **B**. First of all, get permission on the destination. So you need to ask other team to grant permission in their project. use Data viewer if mentioned read or access. use Job User if mention query or job

131. You need to create a copy of a custom Compute Engine virtual machine (VM) to facilitate an expected increase in application traffic due to a business acquisition.
What should you do?
	 - A. Create a Compute Engine snapshot of your base VM. Create your images from that snapshot.
	 - B. Create a Compute Engine snapshot of your base VM. Create your instances from that snapshot.
	 - C. Create a custom Compute Engine image from a snapshot. Create your images from that image.
	 - D. Create a custom Compute Engine image from a snapshot. Create your instances from that image.
	
	 - **D**. VM can be created from snapshot or image. However, To quickly create more than one VM with the same boot disk, create a custom image, then create VMs from that image instead of using a snapshot. (image can be created from snapshot) This match the idea of faciliting business acquisition. https://cloud.google.com/compute/docs/instances/create-start-instance#createsnapshot. General rule, use Snapshot for backup restoration. Use image for create identical VM. 

132. You have deployed an application on a single Compute Engine instance. The application writes logs to disk. Users start reporting errors with the application. You want to diagnose the problem. What should you do?
	 - A. Navigate to Cloud Logging and view the application logs.
	 - B. Connect to the instance's serial console and read the application logs.
	 - C. Configure a Health Check on the instance and set a Low Healthy Threshold value.
	 - D. Install and configure the Cloud Logging Agent and view the logs from Cloud Logging.
	
	 - **D**. The crucial part is "The application writes logs to disk". So log will not be available until install Cloud Logging Agent which is recommended. https://cloud.google.com/logging/docs/agent/logging/installation. You cannot view application log from instance's serial console because it is used to debug boot and networking issues, troubleshooting malfunctiong instance, etc. Not on application level. https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-using-serial-console

133. An application generates daily reports in a Compute Engine virtual machine (VM). The VM is in the project corp-iot-insights. Your team operates only in the project corp-aggregate-reports and needs a copy of the daily exports in the bucket corp-aggregate-reports-storage. You want to configure access so that the daily reports from the VM are available in the bucket corp-aggregate-reports-storage and use as few steps as possible while following Google-recommended practices. What should you do?
	 - A. Move both projects under the same folder.
	 - B. Grant the VM Service Account the role Storage Object Creator on corp-aggregate-reports-storage.
	 - C. Create a Shared VPC network between both projects. Grant the VM Service Account the role Storage Object Creator on corp-iot-insights.
	 - D. Make corp-aggregate-reports-storage public and create a folder with a pseudo-randomized suffix name. Share the folder with the IoT team.
	
	 - **B**. You want VM in `corp-iot-insights` to export report to storage bucket in `corp-aggregate-reports`. Therefore you need to grant VM service account the role of `ObjectCreator` in `corp-aggregate-reports` AKA destination project

134. You built an application on your development laptop that uses Google Cloud services. Your application uses Application Default Credentials for authentication and works fine on your development laptop. You want to migrate this application to a Compute Engine virtual machine (VM) and set up authentication using Google- recommended practices and minimal changes. What should you do?
	 - A. Assign appropriate access for Google services to the service account used by the Compute Engine VM.
	 - B. Create a service account with appropriate access for Google services, and configure the application to use this account.
	 - C. Store credentials for service accounts with appropriate access for Google services in a config file, and deploy this config file with your application.
	 - D. Store credentials for your user account with appropriate access for Google services in a config file, and deploy this config file with your application.
	
	 - **B**. You don't store credentials on any config file. You give service account proper permission. However, you want to create a new service account, do not modify Default Service account because Default Service Account will be used by default by any future instance. This can be a potential risk. 
	
135. You need to create a Compute Engine instance in a new project that doesn't exist yet. What should you do?
	 - A. Using the Cloud SDK, create a new project, enable the Compute Engine API in that project, and then create the instance specifying your new project.
	 - B. Enable the Compute Engine API in the Cloud Console, use the Cloud SDK to create the instance, and then use the --project flag to specify a new project.
	 - C. Using the Cloud SDK, create the new instance, and use the --project flag to specify the new project. Answer yes when prompted by Cloud SDK to enable the Compute Engine API.
	 - D. Enable the Compute Engine API in the Cloud Console. Go to the Compute Engine section of the Console to create a new instance, and look for the Create In A New Project option in the creation form.
	
	 - **A**. When use GCP console, you will not see any of the product navigation until you are in a project. Same for the CDK. You must have a project before your can create an compute engine instance
	
136. Your company runs one batch process in an on-premises server that takes around 30 hours to complete. The task runs monthly, can be performed offline, and must be restarted if interrupted. You want to migrate this workload to the cloud while minimizing cost. What should you do?
	 - A. Migrate the workload to a Compute Engine Preemptible VM.
	 - B. Migrate the workload to a Google Kubernetes Engine cluster with Preemptible nodes.
	 - C. Migrate the workload to a Compute Engine VM. Start and stop the instance as needed.
	 - D. Create an Instance Template with Preemptible VMs On. Create a Managed Instance Group from the template and adjust Target CPU Utilization. Migrate the workload.
	
	 - **C**. No preemptible VM because the task have to restart if interrupted. Also preemptible VM las less than 24 hour

137. You are developing a new application and are looking for a Jenkins installation to build and deploy your source code. You want to automate the installation as quickly and easily as possible. What should you do?
	 - A. Deploy Jenkins through the Google Cloud Marketplace.
	 - B. Create a new Compute Engine instance. Run the Jenkins executable.
	 - C. Create a new Kubernetes Engine cluster. Create a deployment for the Jenkins image.
	 - D. Create an instance template with the Jenkins executable. Create a managed instance group with this template.
		
	 - **A**. When install a standard, popular enviornment as quickly as possible, first choice is to look for Google Cloud Marketplace. Reach for other solution if you want customized environment
	
138. You have downloaded and installed the gcloud command line interface (CLI) and have authenticated with your Google Account. Most of your Compute Engine instances in your project run in the europe-west1-d zone. You want to avoid having to specify this zone with each CLI command when managing these instances.
What should you do?
	 - A. Set the europe-west1-d zone as the default zone using the gcloud config subcommand.
	 - B. In the Settings page for Compute Engine under Default location, set the zone to europeג€"west1-d.
	 - C. In the CLI installation directory, create a file called default.conf containing zone=europeג€"west1ג€"d.
	 - D. Create a Metadata entry on the Compute Engine page with key compute/zone and value europeג€"west1ג€"d.
	
	 - **A**. We are talking about using CLI here so no GCP Console GUI. You can set the default zone/region using `gcloud config set compute/region REGION` or `gcloud config set compute/zone ZONE` https://cloud.google.com/compute/docs/gcloud-compute#set_default_zone_and_region_in_your_local_client
	
139. The core business of your company is to rent out construction equipment at large scale. All the equipment that is being rented out has been equipped with multiple sensors that send event information every few seconds. These signals can vary from engine status, distance traveled, fuel level, and more. Customers are billed based on the consumption monitored by these sensors. You expect high throughput `" up to thousands of events per hour per device `" and need to retrieve consistent data based on the time of the event. Storing and retrieving individual signals should be atomic. What should you do?
	 - A. Create a file in Cloud Storage per device and append new data to that file.
	 - B. Create a file in Cloud Filestore per device and append new data to that file.
	 - C. Ingest the data into Datastore. Store data in an entity group based on the device.
	 - D. Ingest the data into Cloud Bigtable. Create a row key based on the event timestamp.
	
	 - **D**. Looking for a few keywords here. This is IoT. IoT means no-SQL data and usually bigtable. When you want **high throughput** is always bigtable. It is faster than file type database
	
	
140. You are asked to set up application performance monitoring on Google Cloud projects A, B, and C as a single pane of glass. You want to monitor CPU, memory, and disk. What should you do?
	 - A. Enable API and then share charts from project A, B, and C.
	 - B. Enable API and then give the metrics.reader role to projects A, B, and C.
	 - C. Enable API and then use default dashboards to view all projects in sequence.
	 - D. Enable API, create a workspace under project A, and then add projects B and C.
	
	 - **D**. The actual name of this action is no longer called workspace but the concept still applies. To monitor multiple project, you define **scopes** to "you can expand the set of metrics that a project can access by adding other Google Cloud projects to the project's metrics scope". To view the metrics for all of your VMs in a single view, you create another project and then add the target projects as monitored projects. https://cloud.google.com/monitoring/settings#example

141. You created several resources in multiple Google Cloud projects. All projects are linked to different billing accounts. To better estimate future charges, you want to have a single visual representation of all costs incurred. You want to include new cost data as soon as possible. What should you do?
	 - A. Configure Billing Data Export to BigQuery and visualize the data in Data Studio.
	 - B. Visit the Cost Table page to get a CSV export and visualize it using Data Studio.
	 - C. Fill all resources in the Pricing Calculator to get an estimate of the monthly cost.
	 - D. Use the Reports view in the Cloud Billing Console to view the desired cost information.
	
     - **A**. It required a visual representation, so we want to involve some sort of dashboard. Since projects are linked to different billing account, we cannot use billing console, because Reports view provides trends for a single billing account for date range. So as alternative, we need to using BigQuery to export and visualize


142. Your company has workloads running on Compute Engine and on-premises. The Google Cloud Virtual Private Cloud (VPC) is connected to your WAN over a
Virtual Private Network (VPN). You need to deploy a new Compute Engine instance and ensure that no public Internet traffic can be routed to it. What should you do?
	 - A. Create the instance without a public IP address.
	 - B. Create the instance with Private Google Access enabled.
	 - C. Create a deny-all egress firewall rule on the VPC network.
	 - D. Create a route on the VPC to route all traffic to the instance over the VPN tunnel.
	
	 - **A**. Compute Engine need to have public IP address in order to communicate with public internet. So remove public IP (A) is the easiest, straight forward method. You can also create `deny all ingress` firewall rule, which is less idea but works

143. Your team maintains the infrastructure for your organization. The current infrastructure requires changes. You need to share your proposed changes with the rest of the team. You want to follow Google's recommended best practices. What should you do?
	 - A. Use Deployment Manager templates to describe the proposed changes and store them in a Cloud Storage bucket.
	 - B. Use Deployment Manager templates to describe the proposed changes and store them in Cloud Source Repositories.
	 - C. Apply the changes in a development environment, run gcloud compute instances list, and then save the output in a shared Storage bucket.
	 - D. Apply the changes in a development environment, run gcloud compute instances list, and then save the output in Cloud Source Repositories.
	
	 - **B**. The new infrasture will be described in Deployment Manager template. You just need to share template with the team. Compare to Cloud Storage Bucket, a single file with Git commit is best to use Cloud Source Repository. Cloud Source Repositories provides fully featured, private Git repositories hosted on Google Cloud. As for configuration which may require change and see history, using Git will be better than saving different version in Cloud Storage Bucket

144. You have a Compute Engine instance hosting an application used between 9 AM and 6 PM on weekdays. You want to back up this instance daily for disaster recovery purposes. You want to keep the backups for 30 days. You want the Google-recommended solution with the least management overhead and the least number of services. What should you do?
	 - A. 1. Update your instances' metadata to add the following value: snapshotג€"schedule: 0 1 * * * 2. Update your instances' metadata to add the following value: snapshotג€"retention: 30
	 - B. 1. In the Cloud Console, go to the Compute Engine Disks page and select your instance's disk. 2. In the Snapshot Schedule section, select Create Schedule and configure the following parameters: - Schedule frequency: Daily - Start time: 1:00 AM ג€" 2:00 AM - Autodelete snapshots after: 30 days
	 - C. 1. Create a Cloud Function that creates a snapshot of your instance's disk. 2. Create a Cloud Function that deletes snapshots that are older than 30 days. 3. Use Cloud Scheduler to trigger both Cloud Functions daily at 1:00 AM.
	 - D. 1. Create a bash script in the instance that copies the content of the disk to Cloud Storage. 2. Create a bash script in the instance that deletes data older than 30 days in the backup Cloud Storage bucket. 3. Configure the instance's crontab to execute these scripts daily at 1:00 AM.

	 - **B**. To backup Compute Engine regularly, the best option is to use Compute Engine's *create scheduled snapshot* features. You schedule the schedule frequency and retention time (auto delete) https://cloud.google.com/compute/docs/disks/scheduled-snapshots. Compute Engine metadata do not contains info about snapshot Schedule
	
145. Your existing application running in Google Kubernetes Engine (GKE) consists of multiple pods running on four GKE n1`"standard`"2 nodes. You need to deploy additional pods requiring n2`"highmem`"16 nodes without any downtime. What should you do?
	 - A. Use gcloud container clusters upgrade. Deploy the new services.
	 - B. Create a new Node Pool and specify machine type n2ג€"highmemג€"16. Deploy the new pods.
	 - C. Create a new cluster with n2ג€"highmemג€"16 nodes. Redeploy the pods and delete the old cluster.
	 - D. Create a new cluster with both n1ג€"standardג€"2 and n2ג€"highmemג€"16 nodes. Redeploy the pods and delete the old cluster.
	
	 - **B**. Here we want to add a new pod without any downtime. Each node pool is a set of machine that have same configuration including machine type. You can introduce a new type of machince to your cluster by creating a new pool. This process do not stop your running node pool. https://cloud.google.com/kubernetes-engine/docs/tutorials/migrating-node-pool#creating_a_node_pool_with_large_machine_type `gcloud container clusters upgrade` is used to upgrade Kubernetes version.
	
146. You have an application that uses Cloud Spanner as a database backend to keep current state information about users. Cloud Bigtable logs all events triggered by users. You export Cloud Spanner data to Cloud Storage during daily backups. One of your analysts asks you to join data from Cloud Spanner and Cloud
Bigtable for specific users. You want to complete this ad hoc request as efficiently as possible. What should you do?
	 - A. Create a dataflow job that copies data from Cloud Bigtable and Cloud Storage for specific users.
	 - B. Create a dataflow job that copies data from Cloud Bigtable and Cloud Spanner for specific users.
	 - C. Create a Cloud Dataproc cluster that runs a Spark job to extract data from Cloud Bigtable and Cloud Storage for specific users.
	 - D. Create two separate BigQuery external tables on Cloud Storage and Cloud Bigtable. Use the BigQuery console to join these tables through user fields, and apply appropriate filters.
	
	 - **D**. BigQuery can query data stored outside of BigQuery, including Cloud Spanner and BigTable. You can also Join data from multiple Data source in BigQuery, using External Tables. This is a perfect match for this situation. Other options do not Join data but only export data individually

147. You are hosting an application from Compute Engine virtual machines (VMs) in us`"central1`"a. You want to adjust your design to support the failure of a **single Compute Engine zone**, eliminate downtime, and minimize cost. What should you do?
	 - A. Create Compute Engine resources in `us-central1-b`. Balance the load across both `us-central-גa` and `us-central-גb`.
	 - B. Create a Managed Instance Group and specify `us-central1-a` as the zone. Configure the Health Check with a short Health Interval.
	 - C. Create an HTTP(S) Load Balancer. ג€" Create one or more global forwarding rules to direct traffic to your VMs.
	 - D. Perform regular backups of your application. Create a Cloud Monitoring Alert and be notified if your application becomes unavailable. Restore from backups when notified.
	
	 - **A**. The key to this zonal failover support is to have VM across multiple zone and use load balancer to distribute the traffic. the `-a` or `-b` stands for the zone. So you want to create a VM in `us-central1-b` so it can be backup and load balancing for `us-central1-a`
	
148. A colleague handed over a Google Cloud Platform project for you to maintain. As part of a security checkup, you want to review who has been granted the Project
Owner role. What should you do?
	 - A. In the console, validate which SSH keys have been stored as project-wide keys.
	 - B. Navigate to Identity-Aware Proxy and check the permissions for these resources.
	 - C. Enable Audit Logs on the IAM & admin page for all resources, and validate the results.
	 - D. Use the command `gcloud projects get iam policy` to view the current role assignments.
	
	 - **D**. Command `glcoud projects get iam policy` will list all the users and service accounts with their role. You can add `00flter="binding.role:roles/owner` to specify the role. Enable audit log will not give you any status, it will only give you activities
	
149. You are running multiple VPC-native Google Kubernetes Engine clusters in the same subnet. The IPs available for the nodes are exhausted, and you want to ensure that the clusters can grow in nodes when needed. What should you do?
	 - A. Create a new subnet in the same region as the subnet being used.
	 - B. Add an alias IP range to the subnet used by the GKE clusters.
	 - C. Create a new VPC, and set up VPC peering with the existing VPC.
	 - D. Expand the CIDR range of the relevant subnet for the cluster.
	
	 - **D**. When there is no IP address available, you expand the IP range. If you run out of IP addresses in the primary IP address range, you can expand the primary IP address range at any time. https://cloud.google.com/kubernetes-engine/docs/concepts/alias-ips
	
150. You have a batch workload that runs every night and uses a large number of virtual machines (VMs). It is fault-tolerant and can tolerate some of the VMs being terminated. The current cost of VMs is too high. What should you do?
	 - A. Run a test using simulated maintenance events. If the test is successful, use preemptible N1 Standard VMs when running future jobs.
	 - B. Run a test using simulated maintenance events. If the test is successful, use N1 Standard VMs when running future jobs.
	 - C. Run a test using a managed instance group. If the test is successful, use N1 Standard VMs in the managed instance group when running future jobs.
	 - D. Run a test using N1 standard VMs instead of N2. If the test is successful, use N1 Standard VMs when running future jobs.
	
	 - **A**. A very typical case with preemptible VM. The job is fault-tolerant and can tolerated some termincation. Run withing 24 hours. Want to save cost. Perfect for preemptible VM. To test the set up, You can simulate a maintenance event on a VM using either the Google Cloud CLI or an API request. https://cloud.google.com/compute/docs/instances/simulating-host-maintenance
	
151. You are working with a user to set up an application in a new VPC behind a firewall. The user is concerned about data egress. You want to configure the fewest open egress ports. What should you do?
	 - A. Set up a low-priority (65534) rule that blocks all egress and a high-priority rule (1000) that allows only the appropriate ports.
	 - B. Set up a high-priority (1000) rule that pairs both ingress and egress ports.
	 - C. Set up a high-priority (1000) rule that blocks all egress and a low-priority (65534) rule that allows only the appropriate ports.
	 - D. Set up a high-priority (1000) rule to allow the appropriate ports.
	
	 - **A**. Ingress is by default `denied`, Egress is by default `allowed`. So we want to **block all egress explicitly**, and then **allow specific ports** for egress. Also to know that high priority rule will overwrite low pritority rule. So we first set low priority to block all egress, then at the high priority level, allows some port for egress to overwrite.
	
152. Your company runs its Linux workloads on Compute Engine instances. Your company will be working with a new operations partner that does not use Google
Accounts. You need to grant access to the instances to your operations partner so they can maintain the installed tooling. What should you do?
	 - A. Enable Cloud IAP for the Compute Engine instances, and add the operations partner as a Cloud IAP Tunnel User.
	 - B. Tag all the instances with the same network tag. Create a firewall rule in the VPC to grant TCP access on port 22 for traffic from the operations partner to instances with the network tag.
	 - C. Set up Cloud VPN between your Google Cloud VPC and the internal network of the operations partner.
	 - D. Ask the operations partner to generate SSH key pairs, and add the public keys to the VM instances.
	
	 - **A**. Here we want to allow users without Google Account to access and maintain VM. We can use IAP (Identity-Aware Proxy) instead of Google Account. IAP controls access to your App Engine apps and Compute Engine VMs running on Google Cloud. It leverages user identity and the context of a request to determine if a user should be allowed access.  This works with user without google account. https://cloud.google.com/iap/docs/external-identities
	
153. You have created a code snippet that should be triggered whenever a new file is uploaded to a Cloud Storage bucket. You want to deploy this code snippet. What should you do?
	 - A. Use App Engine and configure Cloud Scheduler to trigger the application using Pub/Sub.
	 - B. Use Cloud Functions and configure the bucket as a trigger resource.
	 - C. Use Google Kubernetes Engine and configure a CronJob to trigger the application using Pub/Sub.
	 - D. Use Dataflow as a batch job, and configure the bucket as a data source.
	
	 - **B**. You want the code to only run when file being added to Cloud Storage bucket, so need the ability to scale to zero. Cloud function is a perfet solution. The trigger should be cloud storage bucket
	
154. You have been asked to set up Object Lifecycle Management for objects stored in storage buckets. The objects are written once and accessed frequently for 30 days. After 30 days, the objects are not read again unless there is a special need. The objects should be kept for three years, and you need to minimize cost. What should you do?
	 - A. Set up a policy that uses Nearline storage for 30 days and then moves to Archive storage for three years.
	 - B. Set up a policy that uses Standard storage for 30 days and then moves to Archive storage for three years.
	 - C. Set up a policy that uses Nearline storage for 30 days, then moves the Coldline for one year, and then moves to Archive storage for two years.
	 - D. Set up a policy that uses Standard storage for 30 days, then moves to Coldline for one year, and then moves to Archive storage for two years.
	
	 - **B**. Frequent Access = Standard Storage. No access unless special need = Archive. Nearline, Coldline, Archive cut off are 30days, 90days, and 1 year
	
155. You are storing sensitive information in a Cloud Storage bucket. For legal reasons, you need to be able to **record all requests that read any of the stored data**. You want to make sure you comply with these requirements. What should you do?
	 - A. Enable the Identity Aware Proxy API on the project.
	 - B. Scan the bucket using the Data Loss Prevention API.
	 - C. Allow only a single Service Account access to read the data.
	 - D. Enable Data Access audit logs for the Cloud Storage API.
	
	 - **D**. Record reading of data = Data Access Logs. This log is disabled by default due to the amount of logs
	
156. You are the team lead of a group of 10 developers. You provided each developer with an individual Google Cloud Project that they can use as their personal sandbox to experiment with different Google Cloud solutions. You want to be notified if any of the developers are spending above $500 per month on their sandbox environment. What should you do?
	 - A. Create a single budget for all projects and configure budget alerts on this budget.
	 - B. Create a separate billing account per sandbox project and enable BigQuery billing exports. Create a Data Studio dashboard to plot the spending per billing account.
	 - C. Create a budget per project and configure budget alerts on all of these budgets.
	 - D. Create a single billing account for all sandbox projects and enable BigQuery billing exports. Create a Data Studio dashboard to plot the spending per project.
	
	 - **C**. Mentioned above $500 per developer/project. So we need budget and alert at project level. Export to BigQuery and view is dashboard is about data visualizing and analysis. It does not provide alert. So we need to set a budge per project and enable alerting. 
	
157. You are deploying a production application on Compute Engine. You want to prevent anyone from accidentally destroying the instance by clicking the wrong button. What should you do?
	 - A. Disable the flag `Delete boot disk` when instance is deleted.
	 - B. Enable delete protection on the instance.
	 - C. Disable Automatic restart on the instance.
	 - D. Enable Preemptibility on the instance.
	
	 - **B**. You can set a `deletionProtection` flag to prevent the accidental deletion of VM. *B* describe it well. Note that VM or Compute Engine is different from the persistant disk assigned to VM. A is incorrect

158. Your company uses a large number of Google Cloud services centralized in a single project. All teams have specific projects for testing and development. The
DevOps team needs access to all of the production services in order to perform their job. You want to prevent Google Cloud product changes from broadening their permissions in the future. You want to follow Google-recommended practices. What should you do?

	 - A. Grant all members of the DevOps team the role of Project Editor on the organization level.
	 - B. Grant all members of the DevOps team the role of Project Editor on the production project.
	 - C. Create a custom role that combines the required permissions. Grant the DevOps team the custom role on the production project.
     - D. Create a custom role that combines the required permissions. Grant the DevOps team the custom role on the organization level.
	
	 - **C**. DevOps team only need access to production project, so give scope of project level ONLY. To prevent google change on permission, do not use Basic/Predefined role, so create custom role.

159. You are building an application that processes data files uploaded from thousands of suppliers. Your primary goals for the application are data security and the expiration of aged data. You need to design the application to:
	 * Restrict access so that suppliers can access only their own data.
	 * Give suppliers write access to data only for 30 minutes.
	 * Delete data that is over 45 days old.
	
	 * You have a very short development cycle, and you need to make sure that the application requires minimal maintenance. Which two strategies should you use?(Choose two.)
	
    	 - A. Build a lifecycle policy to delete Cloud Storage objects after 45 days.
    	 - B. Use signed URLs to allow suppliers limited time access to store their objects.
    	 - C. Set up an SFTP server for your application, and create a separate user for each supplier.
    	 - D. Build a Cloud function that triggers a timer of 45 days to delete objects that have expired.
    	 - E. Develop a script that loops through all Cloud Storage buckets and deletes any buckets that are older than 45 days.
    	 - **AB**. Two aspects: 1. Delete after 45 days => Cloud Storage Lifecycle Management 2. Limited Time Access => signed URLs give time limited access with anyone who has URL. https://cloud.google.com/storage/docs/lifecycle#delete and https://cloud.google.com/storage/docs/access-control/signed-urls
	
160. Your company wants to standardize the creation and management of multiple Google Cloud resources using Infrastructure as Code. You want to minimize the amount of repetitive code needed to manage the environment. What should you do?
	 - A. Develop templates for the environment using Cloud Deployment Manager.
	 - B. Use curl in a terminal to send a REST request to the relevant Google API for each individual resource.
	 - C. Use the Cloud Console interface to provision and manage all related resources.
	 - D. Create a bash script that contains all requirement steps as gcloud commands.
	
	 - **A**. Infrastructure as code means managing and provisioning computer data centers trhough machine readable definition files (eg: YAML). Cloud Deployment Manager create a set of resrouces and manage them as a unit, call deployments based on configuration file.  https://cloud.google.com/deployment-manager/docs/quickstart

161. You are performing a monthly security check of your Google Cloud environment and **want to know who has access to view data** stored in your Google Cloud
Project. What should you do?
	 - A. Enable Audit Logs for all APIs that are related to data storage.
	 - B. Review the IAM permissions for any role that allows for data access.
	 - C. Review the Identity-Aware Proxy settings for each resource.
	 - D. Create a Data Loss Prevention job.
	
	 - **B**. We are interested in who has permission to view data, not who has viewed data. So we looking at IAM permission for particular data resource, not data access log

162. Your company has embraced a hybrid cloud strategy where some of the applications are deployed on Google Cloud. A Virtual Private Network (VPN) tunnel connects your Virtual Private Cloud (VPC) in Google Cloud with your company's on-premises network. Multiple applications in Google Cloud need to connect to an on-premises database server, and you want to avoid having to change the IP configuration in all of your applications when the IP of the database changes.
What should you do?
	 - A. Configure Cloud NAT for all subnets of your VPC to be used when egressing from the VM instances.
	 - B. Create a private zone on Cloud DNS, and configure the applications with the DNS name.
	 - C. Configure the IP of the database as custom metadata for each instance, and query the metadata server.
	 - D. Query the Compute Engine internal DNS from the applications to retrieve the IP of the database.
	
	 - **B**. In order for Google Cloud application to access your on permise DB, you on permise DB need to have a DNS, which can be done using Cloud DNS, so that they do not need IP. In this case because it is a private connection, you create a private zone.

163. You have developed a containerized web application that will serve internal colleagues during business hours. You want to ensure that no costs are incurred outside of the hours the application is used. You have just created a new Google Cloud project and want to deploy the application. What should you do?
	 - A. Deploy the container on Cloud Run for Anthos, and set the minimum number of instances to zero.
	 - B. Deploy the container on Cloud Run (fully managed), and set the minimum number of instances to zero.
	 - C. Deploy the container on App Engine flexible environment with autoscaling, and set the value min_instances to zero in the app.yaml.
	 - D. Deploy the container on App Engine flexible environment with manual scaling, and set the value instances to zero in the app.yaml.
	
	 - **B**. We want something that scale to 0. App Engine Flexable do not scale to Zero, cloud run can have minimum instance of 0. Cloud Run for Anthos is an add-on of GKE. For a new project there is not GKE so B. https://cloud.google.com/anthos/run/docs/architecture-overview
	
164. You have experimented with Google Cloud using your own credit card and expensed the costs to your company. Your company wants to streamline the billing process and charge the costs of your projects to their monthly invoice. What should you do?
	 - A. Grant the financial team the IAM role of ג€Billing Account Userג€ on the billing account linked to your credit card.
	 - B. Set up BigQuery billing export and grant your financial department IAM access to query the data.
	 - C. Create a ticket with Google Billing Support to ask them to send the invoice to your company.
	 - D. Change the billing account of your projects to the billing account of your company.
	
	 - **D**. Credit Card is record on billing account. So we want to switch project's billing account to company's billing account. *D* is correct. Other options do not change the billing account therefore not changing the credit card being charged
	
165. You are running a data warehouse on BigQuery. A partner company is offering a recommendation engine based on the data in your data warehouse. The partner company is also running their application on Google Cloud. They manage the resources in their own project, but they need access to the BigQuery dataset in your project. You want to provide the partner company with access to the dataset. What should you do?
	 - A. Create a Service Account in your own project, and grant this Service Account access to BigQuery in your project.
	 - B. Create a Service Account in your own project, and ask the partner to grant this Service Account access to BigQuery in their project.
	 - C. Ask the partner to create a Service Account in their project, and have them give the Service Account access to BigQuery in their project.
	 - D. Ask the partner to create a Service Account in their project, and grant their Service Account access to the BigQuery dataset in your project.
	
	 - **D**. You want other project access your resource. Create Service Account in their project (representing them), and grant that service account permission in your resource. 
	 
166. Your web application has been running successfully on Cloud Run for Anthos. You want to evaluate an updated version of the application with a specific percentage of your production users (canary deployment). What should you do?
	 - A. Create a new service with the new version of the application. Split traffic between this version and the version that is currently running.
	 - B. Create a new revision with the new version of the application. Split traffic between this version and the version that is currently running.
	 - C. Create a new service with the new version of the application. Add an HTTP Load Balancer in front of both services.
	 - D. Create a new revision with the new version of the application. Add an HTTP Load Balancer in front of both revisions.
	
	 - **B**. This works for both Clour Run and Cloud Run for Anthos. You can specify which revisions should receive traffic and to specify traffic percentages that are received by a revision by selectin gthe Service, and go to Revision tab, find Manage Traffic. This is different from App Engine in terms of term, but similar concept. In Cloud run we call it "Revision". https://cloud.google.com/anthos/run/docs/rollouts-rollbacks-traffic-migration

167. Your company developed a mobile game that is deployed on Google Cloud. Gamers are connecting to the game with their personal phones over the Internet. The game sends UDP packets to update the servers about the gamers' actions while they are playing in multiplayer mode. Your game backend can scale over multiple virtual machines (VMs), and you want to expose the VMs over a single IP address. What should you do?
	 - A. Configure an SSL Proxy load balancer in front of the application servers.
	 - B. Configure an Internal UDP load balancer in front of the application servers.
	 - C. Configure an External HTTP(s) load balancer in front of the application servers.
	 - D. Configure an External Network load balancer in front of the application servers.
	
	 - **D**. We are load balancing traffic comming from public access, so need to use External Load Balancer. (Not *B*). This is an UDP traffic (No *C*). SSL proxy is for TCP traffic with SSL offload so no *A*. External Network load balancer stands for External TCP/UDP network load balancer. UDP traffic can only go under Network load balancer

168. You are working for a hospital that stores its medical images in an on-premises data room. The hospital wants to use Cloud Storage for archival storage of these images. The hospital wants an automated process to upload any new medical images to Cloud Storage. You need to design and implement a solution. What should you do?
	 - A. Create a Pub/Sub topic, and enable a Cloud Storage trigger for the Pub/Sub topic. Create an application that sends all medical images to the Pub/Sub topic.
	 - B. Deploy a Dataflow job from the batch template, ג€Datastore to Cloud Storage.ג€ Schedule the batch job on the desired interval.
	 - C. Create a script that uses the gsutil command line interface to synchronize the on-premises storage with Cloud Storage. Schedule the script as a cron job.
	 - D. In the Cloud Console, go to Cloud Storage. Upload the relevant images to the appropriate bucket.
	
	 - **C**. You want to send image to cloud storage bucket for archive. This is a process from on-premise to Cloud Storage. A cron job that use `gsutil` to send image will work. This does not need to do anything when Object is created inside of Cloud Storage. So PubSub won't be practical here. Choice *A* is able automatically doing something when image arrive at Cloud Storage
	
169. Your auditor wants to view your organization's use of data in Google Cloud. The auditor is most interested in auditing who accessed data in Cloud Storage buckets. You need to help the auditor access the data they need. What should you do?
	 - A. Turn on Data Access Logs for the buckets they want to audit, and then build a query in the log viewer that filters on Cloud Storage.
	 - B. Assign the appropriate permissions, and then create a Data Studio report on Admin Activity Audit Logs.
	 - C. Assign the appropriate permissions, and then use Cloud Monitoring to review metrics.
	 - D. Use the export logs API to provide the Admin Activity Audit Logs in the format they want.
	
	 - **A**. Apparently Data Access Log is the thing here. This log is by default disabled so need to be enabled first. You can build a query filter on sink to filter by resource, in this case Cloud Storage
	
170. You received a JSON file that contained a private key of a Service Account in order to get access to several resources in a Google Cloud project. You downloaded and installed the Cloud SDK and want to use this private key for authentication and authorization when performing gcloud commands. What should you do?
	 - A. Use the command gcloud auth login and point it to the private key.
	 - B. Use the command gcloud auth activate-service-account and point it to the private key.
	 - C. Place the private key file in the installation directory of the Cloud SDK and rename it to ג€credentials.jsonג€.
	 - D. Place the private key file in your home directory and rename it to ג€GOOGLE_APPLICATION_CREDENTIALSג€.
	
	 - **B**. Trying to authenticate using service account here rather than a google account. Use `gcloud auth activate-service-account [Account] --key-file=KEY_FILE` to authrozie access to goolge with Service Account. This import credentials from file containing private authorization key, and activate them. https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account
	
171. You are working with a Cloud SQL MySQL database at your company. You need to retain a month-end copy of the database for three years for audit purposes.
What should you do?
	 - A. Set up an export job for the first of the month. Write the export file to an Archive class Cloud Storage bucket.
	 - B. Save the automatic first-of-the-month backup for three years. Store the backup file in an Archive class Cloud Storage bucket.
	 - C. Set up an on-demand backup for the first of the month. Write the backup to an Archive class Cloud Storage bucket.
	 - D. Convert the automatic first-of-the-month backup to an export file. Write the export file to a Coldline class Cloud Storage bucket.
	
	 - **A**. For retention 3 years, we will involve Archive Storage class in storage bucket. Which means that we need to export data to Cloud Storage Bucket. Understand the different between Export and Backup. You backup an instance, you export the instance data. Backup cannot be exported. So *A* is the clear answer. https://cloud.google.com/sql/docs/mysql/backup-recovery/backups

172. You are monitoring an application and receive user feedback that a specific error is spiking. You notice that the error is caused by a Service Account having insufficient permissions. You are able to solve the problem but want to be notified if the problem recurs. What should you do?
	 - A. In the Log Viewer, filter the logs on severity 'Error' and the name of the Service Account.
	 - B. Create a sink to BigQuery to export all the logs. Create a Data Studio dashboard on the exported logs.
	 - C. Create a custom log-based metric for the specific error to be used in an Alerting Policy.
	 - D. Grant Project Owner access to the Service Account.
	
	 - **C**. They key here is to **Be notified**, which indicate an alert. While *AB* is about accessing the error log, but only **C** will configure an alerting.
	
173. You are developing a financial trading application that will be used globally. Data is stored and queried using a relational structure, and clients from all over the world should get the exact identical state of the data. The application will be deployed in multiple regions to provide the lowest latency to end users. You need to select a storage option for the application data while minimizing latency. What should you do?
	 - A. Use Cloud Bigtable for data storage.
	 - B. Use Cloud SQL for data storage.
	 - C. Use Cloud Spanner for data storage.
	 - D. Use Firestore for data storage.
	
	 - **C**. A relational database that serve user globally, require high consistency and low latency, go for cloud spanner
	
174. You are about to deploy a new Enterprise Resource Planning (ERP) system on Google Cloud. The application holds the full database in-memory for fast data access, and you need to configure the most appropriate resources on Google Cloud for this application. What should you do?
	 - A. Provision preemptible Compute Engine instances.
	 - B. Provision Compute Engine instances with GPUs attached.
	 - C. Provision Compute Engine instances with local SSDs attached.
	 - D. Provision Compute Engine instances with M1 machine type.
	
	 - **D**. It mentioned in-memory database fast data access. This is a M type of machine. The trick is to remember M stands for *Memory* so anything that is memory intensive should consider M Type machine. Specifically, https://cloud.google.com/compute/docs/machine-resource describe M machine is good for Medium-large OLAP and in-memory databases such as SAP HANA
	
175. You have developed an application that consists of multiple microservices, with each microservice packaged in its own Docker container image. You want to deploy the entire application on Google Kubernetes Engine so that each microservice can be scaled individually. What should you do?
	 - A. Create and deploy a Custom Resource Definition per microservice.
	 - B. Create and deploy a Docker Compose File.
	 - C. Create and deploy a Job per microservice.
	 - D. Create and deploy a Deployment per microservice.
	
	 - **D**. Deployment object control the deployment process. You want to *scaled microservice individually*, you want to use one Deployment per microservice. Other options are not correct: *A* CRD is used when you have custom resrouce that do not come with Kurbenete. We have docker container. *B* Compose file is a different orchestration than Kurbenete, see https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/What-is-Kubernetes-vs-Docker-Compose-How-these-DevOps-tools-compare.  *C*. Job describe a task, usually involve multiple pods to work together. Having one Job per microservice doesn't make sense

176. You will have several applications running on different Compute Engine instances in the same project. You want to specify at a more granular level the service account each instance uses when calling Google Cloud APIs. What should you do?
	 - A. When creating the instances, specify a Service Account for each instance.
	 - B. When creating the instances, assign the name of each Service Account as instance metadata.
	 - C. After starting the instances, use gcloud compute instances update to specify a Service Account for each instance.
	 - D. After starting the instances, use gcloud compute instances update to assign the name of the relevant Service Account as instance metadata.
	
	 - **A**. When create compute engine instance, both on console or using gcloud, you have a chance to specify Service Account. You can choose and existing one, or create a new one on the spot. This is the easiest way to specify service account for each compute engine. https://cloud.google.com/compute/docs/access/service-accounts#associating_a_service_account_to_an_instance
	
177. You are creating an application that will run on Google Kubernetes Engine. You have identified MongoDB as the most suitable database system for your application and want to deploy a managed MongoDB environment that provides a support SLA. What should you do?
	 - A. Create a Cloud Bigtable cluster, and use the HBase API.
	 - B. Deploy MongoDB Atlas from the Google Cloud Marketplace.
	 - C. Download a MongoDB installation package, and run it on Compute Engine instances.
	 - D. Download a MongoDB installation package, and run it on a Managed Instance Group.
	
	 - **B**. Looking for a managed service so Google Cloud Marketplace is the to go options. It does support SLA (service level agreement)
	
178. You are managing a project for the Business Intelligence (BI) department in your company. A data pipeline ingests data into BigQuery via streaming. You want the users in the BI department to be able to run the custom SQL queries against the latest data in BigQuery. What should you do?
	 - A. Create a Data Studio dashboard that uses the related BigQuery tables as a source and give the BI team view access to the Data Studio dashboard.
	 - B. Create a Service Account for the BI team and distribute a new private key to each member of the BI team.
	 - C. Use Cloud Scheduler to schedule a batch Dataflow job to copy the data from BigQuery to the BI team's internal data warehouse.
	 - D. Assign the IAM role of BigQuery User to a Google Group that contains the members of the BI team.
	
	 - **D**. Assign IAM role to group and add member to the group is the approach. To run the custom query, `role/bigquery.user` is appropriate. It allow running query against bigquery table. Viewing dashboard do not give you ability to run custom query. Permission to Dashboard != Permission to Dataset

179. Your company is moving its entire workload to Compute Engine. Some servers should be accessible through the Internet, and other servers should only be accessible over the internal network. All servers need to be able to talk to each other over specific ports and protocols. The current on-premises network relies on a demilitarized zone (DMZ) for the public servers and a Local Area Network (LAN) for the private servers. You need to design the networking infrastructure on
Google Cloud to match these requirements. What should you do?

	 - A. 1. Create a single VPC with a subnet for the DMZ and a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public ingress traffic for the DMZ.
	 - B. 1. Create a single VPC with a subnet for the DMZ and a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public egress traffic for the DMZ.
	 - C. 1. Create a VPC with a subnet for the DMZ and another VPC with a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public ingress traffic for the DMZ.
	 - D. 1. Create a VPC with a subnet for the DMZ and another VPC with a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public egress traffic for the DMZ.
	
	 - **A**. "All server need to talk to each over over specific port and protocal" means internal communication. Instance withing the same VPC can communicate privately. So We know we need **One VPC** Only. Then we have one DMZ for public access and one LAN for internal access. They can fall under **two subnets**. Since DMZ need access through internet (Ingress Access), we set `allow-public-ingress` firewall rule for DMZ. Finally, note that subnet within VPC can communicate internally if proper firewall is set. By default we have `default-allow-internal`
	
180. You have just created a new project which will be used to deploy a globally distributed application. You will use Cloud Spanner for data storage. You want to create a Cloud Spanner instance. You want to perform the first step in preparation of creating the instance. What should you do?
	
	 - A. Enable the Cloud Spanner API.
	 - B. Configure your Cloud Spanner instance to be multi-regional.
	 - C. Create a new VPC network with subnetworks in all desired regions.
	 - D. Grant yourself the IAM role of Cloud Spanner Admin.
	
	 - **A**. The first step to use any google resource is always to turn on the relative API. In GCP Console sometimes the API is already on but always good to confirm. In GLI you need to manually turn it on.
	
181. You have created a new project in Google Cloud through the gcloud command line interface (CLI) and linked a billing account. You need to create a new Compute
Engine instance using the CLI. You need to perform the prerequisite steps. What should you do?

	 - A. Create a Cloud Monitoring Workspace.
	 - B. Create a VPC network in the project.
	 - C. Enable the compute googleapis.com API.
	 - D. Grant yourself the IAM role of Computer Admin.
	
	 - **C**. As mentioned in other questions, nothing can be done before activating API. API > IAM
	
182. Your company has developed a new application that consists of multiple microservices. You want to deploy the application to Google Kubernetes Engine (GKE), and you want to ensure that the cluster can scale as more applications are deployed in the future. You want to avoid manual intervention when each new application is deployed. What should you do?
	 - A. Deploy the application on GKE, and add a HorizontalPodAutoscaler to the deployment.
	 - B. Deploy the application on GKE, and add a VerticalPodAutoscaler to the deployment.
	 - C. Create a GKE cluster with autoscaling enabled on the node pool. Set a minimum and maximum for the size of the node pool.
	 - D. Create a separate node pool for each application, and deploy each application to its dedicated node pool.
	
	 - **A**. HorizontalPodAutoscaler adjust total resources of Pod based on workload. When new application deployed (may add more microservice), horizontal pod autoscaler has ability to automatically scale to add more pods for running more microservice. Vertical Scaling is about re-provisioning resources between microservice. Cluster autoscaling can increase the size of the cluster but as we don't know how big the application go, we can't set maximum size of node pool so *C* is incorrect. *D* involve manual intervention

183. You need to manage a third-party application that will run on a Compute Engine instance. Other Compute Engine instances are already running with default configuration. Application installation files are hosted on Cloud Storage. You need to access these files from the new instance without allowing other virtual machines (VMs) to access these files. What should you do?

	 - A. Create the instance with the default Compute Engine service account. Grant the service account permissions on Cloud Storage.
	 - B. Create the instance with the default Compute Engine service account. Add metadata to the objects on Cloud Storage that matches the metadata on the new instance.
	 - C. Create a new service account and assign this service account to the new instance. Grant the service account permissions on Cloud Storage.
	 - D. Create a new service account and assign this service account to the new instance. Add metadata to the objects on Cloud Storage that matches the metadata on the new instance.
	
	 - **C**. "Without allowing other instances" indicate that we need permission different than other VM. Because permission is related to Service Account, we need a new, independent service account and grant it the correct permissions to Cloud Storage.
	
184. You need to configure optimal data storage for files stored in Cloud Storage for minimal cost. The files are used in a mission-critical analytics pipeline that is used continually. The users are in Boston, MA (United States). What should you do?
	 - A. Configure regional storage for the region closest to the users. Configure a Nearline storage class.
	 - B. Configure regional storage for the region closest to the users. Configure a Standard storage class.
	 - C. Configure dual-regional storage for the dual region closest to the users. Configure a Nearline storage class.
	 - D. Configure dual-regional storage for the dual region closest to the users. Configure a Standard storage class.
	
	 - **B**. The data is used continually so a standard storage class is critical. I would go with Regional storage because users are in a single city. A regional storage would be best due to its low latency, better performace and cost effective. Regional storage also has failover for single zone failure, which is enough to cover one city.

185. You are developing a new web application that will be deployed on Google Cloud Platform. As part of your release cycle, you want to test updates to your application on a small portion of real user traffic. The majority of the users should still be directed towards a stable version of your application. What should you do?
	
	 - A. Deploy the application on App Engine. For each update, create a new version of the same service. Configure traffic splitting to send a small percentage of traffic to the new version.
	 - B. Deploy the application on App Engine. For each update, create a new service. Configure traffic splitting to send a small percentage of traffic to the new service.
	 - C. Deploy the application on Kubernetes Engine. For a new release, update the deployment to use the new version.
	 - D. Deploy the application on Kubernetes Engine. For a new release, create a new deployment for the new version. Update the service to use the new deployment.
	
	 - **A**. App Engine provide versioning and traffic splitting between version. This is done within same service, no need to create antoerh service
	 
186. You need to add a group of new users to Cloud Identity. Some of the users already have existing Google accounts. You want to follow one of Google's recommended practices and avoid conflicting accounts. What should you do?
	 - A. Invite the user to transfer their existing account.
	 - B. Invite the user to use an email alias to resolve the conflict.
	 - C. Tell the user that they must delete their existing account.
	 - D. Tell the user to remove all personal email from the existing account.
	
	 - **A**. We want to convert user's existing "consumer" account to a "managed" account. You can use **transfer tool for unmanaged users** to do that. Because consumer account is controlled by user who create them, not buy your organization. And creating an alias will not give company control over that. You need to transfer that into managed account. Otherwise their username can not be reused and managed by company

187. You need to manage a Cloud Spanner instance for best query performance. Your instance in production runs in a single Google Cloud region. You need to improve performance in the shortest amount of time. You want to follow Google best practices for service configuration. What should you do?
	 - A. Create an alert in Cloud Monitoring to alert when the percentage of high priority CPU utilization reaches 45%. If you exceed this threshold, add nodes to your instance.
	 - B. Create an alert in Cloud Monitoring to alert when the percentage of high priority CPU utilization reaches 45%. Use database query statistics to identify queries that result in high CPU usage, and then rewrite those queries to optimize their resource usage.
	 - C. Create an alert in Cloud Monitoring to alert when the percentage of high priority CPU utilization reaches 65%. If you exceed this threshold, add nodes to your instance.
	 - D. Create an alert in Cloud Monitoring to alert when the percentage of high priority CPU utilization reaches 65%. Use database query statistics to identify queries that result in high CPU usage, and then rewrite those queries to optimize their resource usage.
	
	 - **C**. The explaination is here https://cloud.google.com/spanner/docs/cpu-utilization#recommended-max. The CPU utilization threshold is 45% for Multi-region and 65% for Single Region. It is also recommended to first increase the computing capacity (scale up), and then evaluate the root cause. So *C* is correct

188. Your company has an internal application for managing transactional orders. The application is used exclusively by employees in a single physical location. The application requires strong consistency, fast queries, and ACID guarantees for multi-table transactional updates. The first version of the application is implemented in PostgreSQL, and you want to deploy it to the cloud with minimal code changes. Which database is most appropriate for this application?
	 - A. BigQuery
	 - B. Cloud SQL
	 - C. Cloud Spanner
	 - D. Cloud Datastore
	
	 - **B**. Straight forward, single physical location with implementation on PSQL. use Cloud SQL
	
189. You are assigned to maintain a Google Kubernetes Engine (GKE) cluster named 'dev' that was deployed on Google Cloud. You want to manage the GKE configuration using the command line interface (CLI). You have just downloaded and installed the Cloud SDK. You want to ensure that future CLI commands by default address this specific cluster What should you do?
	
	 - A. Use the command gcloud config set container/cluster dev.
	 - B. Use the command gcloud container clusters update dev.
	 - C. Create a file called gke.default in the ~/.gcloud folder that contains the cluster name.
	 - D. Create a file called defaults.json in the ~/.gcloud folder that contains the cluster name.
	
	 - **A**. It is never good idea to edit config file for SDK. Use gcloud command instead. `gcloud config set container/cluster CLUSTER_NAME` set the default cluster. https://cloud.google.com/kubernetes-engine/docs/how-to/managing-clusters
	
190. The sales team has a project named Sales Data Digest that has the ID acme-data-digest. You need to set up similar Google Cloud resources for the marketing team but their resources must be organized independently of the sales team. What should you do?
	 - A. Grant the Project Editor role to the Marketing team for acme-data-digest.
	 - B. Create a Project Lien on acme-data-digest and then grant the Project Editor role to the Marketing team.
	 - C. Create another project with the ID acme-marketing-data-digest for the Marketing team and deploy the resources there.
	 - D. Create a new project named Marketing Data Digest and use the ID acme-data-digest. Grant the Project Editor role to the Marketing team.
	
	 - **C**. organize resource independently == in a seperate project. So need to create a new project. Project ID has to be unique so cannot reuse `acme-data-digest`

191. You have deployed multiple Linux instances on Compute Engine. You plan on adding more instances in the coming weeks. You want to be able to access all of these instances through your SSH client over the internet without having to configure specific access on the existing and new instances. You do not want the
Compute Engine instances to have a public IP. What should you do?

	 - A. Configure Cloud Identity-Aware Proxy for HTTPS resources.
	 - B. Configure Cloud Identity-Aware Proxy for SSH and TCP resources
	 - C. Create an SSH keypair and store the public key as a project-wide SSH Key.
	 - D. Create an SSH keypair and store the private key as a project-wide SSH Key.
	
	 - **B**. Identiy Aware Proxy (IAP) have TCP forwarding enable admin access to VM instances that do not have external IP address or do not permit direct access over internet. IAP TCP forwarding establish encrypted tunnel over which you can forward SSH, RDP and other traffic to VM instances. IAP TCP forwarding use IP range of  `35.235.240.0/20` https://cloud.google.com/iap/docs/using-tcp-forwarding
	
192. You have created an application that is packaged into a Docker image. You want to deploy the Docker image as a workload on Google Kubernetes Engine. What should you do?

	 - A. Upload the image to Cloud Storage and create a Kubernetes Service referencing the image.
	 - B. Upload the image to Cloud Storage and create a Kubernetes Deployment referencing the image.
	 - C. Upload the image to Container Registry and create a Kubernetes Service referencing the image.
	 - D. Upload the image to Container Registry and create a Kubernetes Deployment referencing the image. 
	
	 - **D**. Standard Practice for GKE docker container is to upload image to Container Registry. Then you create deployment referencing the image. A deployment is responsible for keeping a set of pods running. A service is responsible for enabling network access to a set of pods.

193. You are using Data Studio to visualize a table from your data warehouse that is built on top of BigQuery. Data is appended to the data warehouse during the day.
At night, the daily summary is recalculated by overwriting the table. You just noticed that the charts in Data Studio are broken, and you want to analyze the problem. What should you do?
	 - A. Review the Error Reporting page in the Cloud Console to find any errors.
	 - B. Use the BigQuery interface to review the nightly job and look for any errors.
	 - C. Use Cloud Debugger to find out why the data was not refreshed correctly.
	 - D. In Cloud Logging, create a filter for your Data Studio report.
	
	 - **D**. Cloud logging cannot filter Data Studio Report directly but we can analyze data source that generate Data Studio Report, in this case Big Query. Compared to B who can also debug errors, Cloud Logging to analyze the logs will provide you with a more holistic view of any issues that may be affecting your report, rather than focusing solely on the BigQuery job that updates the table. Additionally, Cloud Logging is a more general-purpose tool that can be used to troubleshoot issues with a wide range of services

194. You have been asked to set up the billing configuration for a new Google Cloud customer. Your customer wants to group resources that share common IAM policies. What should you do?
	 - A. Use labels to group resources that share common IAM policies.
	 - B. Use folders to group resources that share common IAM policies.
	 - C. Set up a proper billing account structure to group IAM policies.
	 - D. Set up a proper project naming structure to group IAM policies.
	
	 - **B**. The keyword here is **group resrouces that share common IAM policies**. This is a typical use of *Folder*. "Folders allow you to group these resources on a per-department basis. Folders are used to group resources that share common IAM policies". This question has nothing to do with billing. https://cloud.google.com/resource-manager/docs/creating-managing-folders
 


195. You have been asked to create robust Virtual Private Network (VPN) connectivity between a new Virtual Private Cloud (VPC) and a remote site. Key requirements include dynamic routing, a shared address space of 10.19.0.1/22, and no overprovisioning of tunnels during a failover event. You want to follow Google- recommended practices to set up a high availability Cloud VPN. What should you do?

	 - A. Use a custom mode VPC network, configure static routes, and use active/passive routing.
	 - B. Use an automatic mode VPC network, configure static routes, and use active/active routing.
	 - C. Use a custom mode VPC network, use Cloud Router border gateway protocol (BGP) routes, and use active/passive routing.
	 - D. Use an automatic mode VPC network, use Cloud Router border gateway protocol (BGP) routes, and configure policy-based routing.
	
	 - **C**. We what to specify the IP range so need to configure with custom mode VPC (https://cloud.google.com/vpc/docs/vpc#subnet-ranges). Google recommend dynamic routing with broder gateway protocol (BGP) and HA VPN. For tunnel configuration, since we have *no overprovisioning of tunnels*, it means single HA VPN gateway, we use *active/passive* tunnel. (https://cloud.google.com/network-connectivity/docs/vpn/concepts/best-practices) active/passive means primary resource available most of time and secondary resrouce standby in case primary fail. This prevent overprovisioning

196. You are running multiple microservices in a Kubernetes Engine cluster. One microservice is rendering images. The microservice responsible for the image rendering requires a large amount of CPU time compared to the memory it requires. The other microservices are workloads that are optimized for n1-standard machine types. You need to optimize your cluster so that all workloads are using resources as efficiently as possible. What should you do?

	 - A. Assign the pods of the image rendering microservice a higher pod priority than the other microservices.
	 - B. Create a node pool with compute-optimized machine type nodes for the image rendering microservice. Use the node pool with general-purpose machine type nodes for the other microservices.
	 - C. Use the node pool with general-purpose machine type nodes for the image rendering microservice. Create a node pool with compute-optimized machine type nodes for the other microservices.
	 - D. Configure the required amount of CPU and memory in the resource requests specification of the image rendering microservice deployment. Keep the resource requests for the other microservices at the default.
	
	 - **B**. Need to have identical machine type inside of a node pool. So we need two node pool, one for CPU intensive workloads and one for other. The compute-optimized machine type node will run rendering image and other general purpose type node will run other microservices.

197. Your organization has three existing Google Cloud projects. You need to bill the Marketing department for only their Google Cloud services for a new initiative within their group. What should you do?
	 - A. 1. Verify that you are assigned the Billing Administrator IAM role for your organization's Google Cloud Project for the Marketing department. 2. Link the new project to a Marketing Billing Account.
	 - B. 1. Verify that you are assigned the Billing Administrator IAM role for your organization's Google Cloud account. 2. Create a new Google Cloud Project for the Marketing department. 3. Set the default key-value project labels to department:marketing for all services in this project.
	 - C. 1. Verify that you are assigned the Organization Administrator IAM role for your organization's Google Cloud account. 2. Create a new Google Cloud Project for the Marketing department. 3. Link the new project to a Marketing Billing Account.
	 - D. 1. Verify that you are assigned the Organization Administrator IAM role for your organization's Google Cloud account. 2. Create a new Google Cloud Project for the Marketing department. 3. Set the default key-value project labels to department:marketing for all services in this project.
	
	 - **A**. Here we only talk about billing. Nothing mentioned that you need to create project so B C D are out. As a billing account admin at project level, you can link project to billing account.

