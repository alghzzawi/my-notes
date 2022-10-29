# Serverless Functions

#### Serverless is a cloud application development and execution model that lets developers build and run code without managing servers

## What is serverless?

#### Serverless is a cloud computing application development and execution show that empowers developers to construct and run application code without provisioning or overseeing servers or backend infrastructure. Serverless lets developers put all their center into composing the most excellent front-end application code and business logic they can. All developers ought to do is type in their application code and send it to holders overseen by a cloud benefit supplier. The cloud supplier handles the rest, provisioning the cloud infrastructure required to run the code and scaling the infrastructure up and down on request as required. The cloud supplier is additionally dependable for all schedule foundation management and maintenance such as working framework overhauls and patches, security management, capacity arranging, framework monitoring and more.

---

## Serverless is more than just FaaS

#### Function as a Service, or FaaS, is a cloud computing service that enables developers to run code or containers in response to specific events or requests, without specifying or managing the infrastructure required to run in code.

#### FaaS is a central, serverless computing model, and the two terms are often used interchangeably. But without a server it is much more than FaaS. Serverless is a complete set of services that can respond to specific events or requests, scale to zero when not in use - that are provisioned, managed, and billed by the cloud provider and are invisible to developers. In addition to FaaS, these services include:

- #### __Serverless databases and storage__: Databases (SQL and NoSQL) and storage (particularly object storage) are the foundation of the data layer. A serverless approach to these technologies involves transitioning away from provisioning “instances” with defined capacity, connection and query limits, and moving toward models that scale linearly with demand in both infrastructure and pricing.

- #### __Event streaming and messaging__: Serverless architectures are well-suited for event-driven and stream-processing workloads most notably the open source Apache Kafka event streaming platform.

- #### __API gateways__: API gateways act as proxies to web actions and provide HTTP method routing, client ID and secrets, rate limits, CORS, viewing API usage, viewing response logs, and API sharing policies.

---

## Pros and cons of serverless


### Pros

#### Given all of the preceding, it should be no surprise that serverless computing offers a number of technical and business benefits to individual developers and enterprise development teams.

#### __Improved developer productivity__: As noted above, serverless enables development teams to focus on writing code, not managing infrastructure. It gives developers much more time to innovate and optimize their front-end application functionality and business logic.

#### __Pay for execution only__: The meter starts when the request is made, and ends when execution finishes. Compare this to the infrastructure as a service (IaaS) compute model, where customers pay for the physical servers, virtual machines (VMs) and other resources required to run applications, from the time they provision those resources until the time they explicitly decommission them.

#### __Develop in any language__: Serverless is a polyglot environment, enabling developers to code in any language or framework—Java, Python, JavaScript, node.js—with which they're comfortable.

#### Streamlined development/DevOps cycles. Serverless simplifies deployment and, in a larger sense, simplifies DevOps because developers don't spend time defining infrastructure required to integrate, test, deliver and deploy code builds into production.

#### Cost-effective performance. For certain workloads—embarrassingly parallel processing, stream processing, certain data processing tasks—serverless computing can be both faster and more cost-effective than other forms of compute.

#### Usage visibility. Serverless platforms provide near-total visibility into system and user times and can aggregate usage information systematically.

### Cons
#### With so much to like about serverless, organizations are using it for a wide variety of applications (see Figure 2 below). But there are drawbacks—some of which are related to specific applications, and others which are universal.

#### __Unacceptable latency for certain applications__: Because serverless architectures forgo ongoing processes in favor of scaling up and down to zero, they also sometimes need to start up from zero to serve a new request. For many applications the resultant delay would not be detrimental or even noticeable to users. But for others—say, a financial trading application—this cold-start latency might be unacceptable.

#### __Higher costs for stable or predictable workloads__: Because serverless scales up and down on demand in response to workload, it offers significant cost savings for spiky workloads. But it does not offer the same savings for workloads characterized by predictable, steady or long-running processes; in these cases, a traditional server environment might be simpler and more cost-effective.

#### __Monitoring and debugging issues__: These operational tasks are challenging in any distributed system, but serverless architecture (or microservices architecture, or a combination of the two) only exacerbates the complexity. For example, teams may find it difficult or impossible to monitor or debug serverless functions using existing tools or processes.

#### __Vendor lock-in__: As noted, one of the biggest advantages of serverless is that the cloud provider manages all the computing resources. While this frees up considerable time for developers to focus on writing and improving their code, it also means that migrating code to a new cloud provider could prove challenging. Many cloud provider’s serverless platforms are designed to provide an ecosystem of managed cloud services and are not portable like virtual machines (VMs) or Docker containers. Application code that triggers several services offered by one cloud provider’s serverless platform might have to be partially or completely rewritten to get get the same results in another provider’s platform.

