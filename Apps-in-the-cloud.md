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
