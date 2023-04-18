# App Engine
Fully managed, serverless platform for developing and hosting web apps at scale.
You can choose popular languages, libs and frameworks.
- You can upload your code and Google will sort what lang.

## Built in services and APIs
- NoSQL datastores.
- Hwalth checks.
- Memcache.
- App logging.
- Load balancing.
- User auth API.

App engine also offer Software developing kits (SDK).

## Cloud console's web-based interface
- Create new apps.
- Configure domain names.
- Change which version is live.
- Examine access and error logs.

## Security
Security Command Center keeps web apps safe. You can scan your apps for threats.

## App Engine evironments
### Standard
- Based on containers instances running on googles infrastructure.
- Containers are pre-configured, includes libs and supoirt App engines standard API.
- Persistent storage with queries, sorting and transactions.
- Automatic scaling and load balancing.
- Asynchronous task queues for performing work outside the scope of a request.
- Scheduöed tasks for triggering events at specified times or regular intervals.
- Integrations with other Google Cloud services and APIs.

There are a few musts to use standards environments:
- Use specified versions of Java, Python, PHP, Go, Node.js and Ruby.
- Application must conform to sandbox constraints that are dependent on runtime.

Standard environment lifecycle:
1. Develop web app and test locally => 2. Deploy to App Engine with SDK => 3. App engine scales and services the app.

### Flexible
Runs in docker containers on Google cloud compute engine VMs.
In this case App Engine manages compute engine machines for you.
This means:
- Instances are health-checked, healed and co-located.
- Critical, backward-compatible updates are automatically applied to the underlying OS.
- VM instances are automatically located bu geographical region according to the settings in your project.
- VM instances are restarted on a weekly basis.

The flexible env supports:
- Microservices.
- Authorization.
- SQL & NoSQL databses.
- Traffic splitting.
- Logging.
- Search.
- Versioning.
- Security scanning.
- Memcache.
- Content delivery networks.

Flexible also supports:
- Benefit from custom configurations and libraries, while focusing on writing code.
- Customize the runtime and the operating system of your VM. Standard runtimes include Python, Java, Go, Node.js, PHP, .NET and Ruby.
- Customize or provide runtime by supplying a custom Docker image or Dockerfile.

![alt text](https://github.com/lura00/GCP_how-to/blob/main/standard-flexible-env-compare.PNG)

## Google Cloud API management tools
### APIs
- A Clean, well-defined interface.
- Underlying implementation can change.
- Changes to the API are made with versions.

Google Cloud supports 3 API management tools.
- Cloud Endpoint.
- Apigee Edge.
- API Gateway.

### Cloud Endpoint
- Distributed API management system.
- Provides an API console, hosting, logging, monitoring, and other features.
- Use with any APIs that support the OpenAPI specs.
- Support apps running in App Engine, GKE and Compute Engine.
- Clients include Android, iOS and Javascript.

### API Gateway
-  Backend implementations can vary for a single service provider.
-  Provide secure access to your backend services through a well-defined REST API.
-  Clients consume your REST APIs to implement standalone apps.

### Apigee Edge
- Specific focus on business problems, like rate limiting, quotas and analytics.
- Many Apigee Edge users provice a software service to other companies.
- Backend services for Apigee Edge don't need to be in Google Cloud.

## Cloud Run
- A managed compute platform that can run stateless containers. Used for ex in pub/sub-events.
- Serverless, removing the need for infrastructure management.
- Built on Knative, an open API and runtime environment built on Kubernetes.
- Can automatically scale up and down from zero almost instantaneously, charging only for the resources used.

Cloud Run workflow:
1. Write your code, source code => 2. Build and package your code to an container image app and push to => 3. Artifact Registry, deploy on Cloud Run.
- Cloud Run can only deploy apps that are stored in an Artifact Registry.
- You can build and push your own code/images to an artifactory and deploy it, deploy an image that is already in the Artifact Registry.
- Once you have deployed you get a uniqe HTTPS URL back.

You can work from your source code or directly push a container. If you work with source code Cloud Run will build a container of it. 

Flow of Cloud Run web apps.

https://***.run.app or 
https://your.domain 
==>                    
Client ==HTTPS==> [ Cloud Run Proxy ==HTTP==> Container]

Cloud Run fixing ssl certificate by itself.

You pay for what you use or what is still active.

Acceptable programming languages:
- Java
- Python
- Node.js
- PHP
- Go
- C++

As long as your app handles web requests.
