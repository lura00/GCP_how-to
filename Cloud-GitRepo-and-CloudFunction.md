## Development in the Cloud

Git Repo in GCP.
  Use IAM to set authorization.
Cloud Git Repo is fully functional Git repos and very easy collab if you have an web app that for example runs on App Engine or Compute Engine.

You can have private Git repon as well.

If you have a repo on other Git Repo, like github, you can easuly migrate it to Cloud Repo just as you would migrate from Github to Gitlab.

### CLoud Functions
- Lightweight, event-based, asynchronous compute solution.
- Allows you to create small, single-purpose functions that respond to cloud events without the need to manage a server or a runtime environment.
- Use these functions to construct apps from bite-sized business logic and connect and extend cloud services.
- Billed to the nearest 100 milliseconds, and only while your code is running.
- Supports writing source code in a number of programming languages, including Node.js, Python, Go, Java, .Net Core, Ruby and PHP.
- Events from Cloud Storage and Pub/Sub can trigger Cloud Functions asynchronously, or use HTTTP invocation for synchronous execution.


## Deployment: IaC

### Terraform
- Create a template file using HashiCorp Configuration Language (HCL) that describes what the components of the environment should look like.
- Terraform uses that template to determine the actions needed to create the environment your template describes.
- Use Terraform to update the environment to match the change.
- Store and version-control Terraform templates in Cloud Source Repos.
