# Article 1: Serverless Computing: State-of-the-Art, Challenges and Opportunities

## Abstract
- lightweight and simplicity of management
- computing unit now becomes the function level
- balance high-perf scheduling with low cost
- In this article:
  + Survey of serverless computing
  + infrastructure characteristic
  + Challenges and their address
  + Serverless are believed to dominate the cloud platforms
 
## 1. Introduction
- dev needs to write cloud functions in a high-level lang
- set params and upload to serverless platform
- API and HTTP requests to execute task
- Infrastructure resources as platforms shield such details on behalf of them are relieved
- Cloud function are invoked as unit of exe
- Function as a Service FaaS, making application as a service without infra complexity
- Serverless providers support application dependencies services(Baas, OOS)
- help developers focus on the core logic of the application - reduce the cost by having ms runtime unit
- Many cloud providers has shown their movement AWS lambda, IBM Cloud Function Openwhisk, Ms Azure Fucntion,...
- video processing, machine learning, linear algebra, data analytics, distributed computing
- Many studying about optimization of Serverless's start latency - one of the major chanllenges

### serverless vs serverful
- application characteristics and runtime environment
- adaptations to the accommodation of serverless requirements
  + network communication is quite complicated and large
- Serverless Egde computing can help but still left opened
- Then, we conclude some directions that could be promising in future research but have not been noticed widely yet.

# 2. Background
- evolution of virualization technology
- confusion concepts with serverless definition

## 2.1 Evolotion:
- Virtual Machine (VM), Container and Serverless.
- VMs andcontainers promotes the birth of cloud computing
- Serverless is more lightweight and flexible
![image](https://github.com/user-attachments/assets/6d8d8667-99ab-4382-ac3f-74ce09a8727e)
- frees developers from the burden of resource management and complex configurations

## 2.2 Related Concepts
- Unikernels provide a more lightweight hypervisor
- Cloud Native is new development method and tech achi
- supports public private hybrid cloud
- Cloud-native app are organized in a microservice-based framework
- lightweight protocols — Remote Procedure Calls or Service Mesh

# 3. Characteristic and Challenges
## 3.1 Characteristic or Serverless
- function programming:
  + develop the function based on the rules of platform providers
  + Deploy the function to that platform
  + Platforms save in db then push the runtime to repo and return to programmers the URls
- Function Serving:
  + use returned URL or configured triggering event to invoke through API gateway provided by the platform
  + fetches the function from db and prepare the runtime env called sandbox
  + Platfomr initialize the app env(class files) and execute the function
- Hostless and elastic:
  + do not need to work with servers
  + payoff is new challenges: resource occupation and exe time
  + count on the resource being used
- Lightweight:
  + small number of serverless func
  + Developers can focus on the app logic and other concerns are shifted to the cloud providers
  + Dev often choose large, complex functions
  + This is still a open research challenge
- Statelessness:
  + functions often run on stateless container
  + machine learning, graph algorithms, and interactive big data computation motivated works to exploit stateful serverless computing
- Short But Variable Execution Times:
  + Lambda limit 15mins and bill in 100ms unit
- Poor Intra-Function Parallelism:
  + Functions can be process at the same time and share data via persistent storage
  + parallelizing the functions and executing them within a single function instance might be more suitable and economic, especially for compute-intensive workloads
- Migration:
  + fetched remotely, required an exe env to init fucntion invocation
  + functions tend to have startup-cost which makes migration unappealing
- Separated Containers:
  + isolate and exe the function in separeted containers
  + Leading to higher latency and more network communication pressure
- Burstiness:
  + Workloads fluctuate their degress
  + 81% of the tested workloads are bursty
  + Cloud computing, App often run smoothly and live for long time.
## 3.2 Existing Challanges
### 3.2.1 Startup Latency
- Cold Start is more cosly than Warm start
- sandbox env runs wrapped program that contains the target app fucntion
- Then after this, the func is ready - application initialization
- cache-based method, optimization on the sandbox init, check-point optimization
- sandbox init optimization by using Unikernel and more lightweight hypervisor
- save the state of instance in image and inject that in a running application can save startup time
### 3.2.2 Isolation
### 3.2.3 Scheduling Policy
### 3.2.4 Facility
### 3.2.5 Fault Tolerance

# 4 Framworks in Practice
## 4.1 Typical Open-Source Framworks
## 4.2 Performance on Challenges

# 5 Reasearch Opportunities
## 5.1 Machine Learning for Resouce Management
## 5.2 Integration with Edge Computing
## 5.3 Developments of Benchmarking

# 6 Conclusion
