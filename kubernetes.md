# Container Orchestration with Kubernetes

## Transition from VMs to Containers

### VMs
In the past years, VMs (Virtual Machines) were the main machanism to host an application. VMs encapsulate the code, configuration files, and dependencies necessary to execute the application.

In essence, a VM is composed of an __operating system__ (OS) with a set of pre-installed libraries and packages. During execution, the __application__ utilizes an OS filesystem, resources, and packages.

A set of VMs are hosted on a __hypervisor__ which provides the virtualization of the server __infrastructure__. However, there is one downside to this mechanism: It is not efficient enough because it needs to replicate the OS for each VM. There was a clear need to optimize the usage of the available infrastructure. As a result, the virtualization of the Operating System was introduced. 

### Contrainers
__Contrainers__ represent the bare minimum an application requires tfor a successful execution e.g. code, config files, and dependencies. By default, there is a better usage of available infrastructure.

Multiple VMs on a hypervisor are replaced by multiple contrainers running on a single host operating system. The process in the contrainers are completely isolated but are able to access the OS filesystem, resources, and packages. The creation and execution of containers is delegated to a contrainer management tool, such as Docker.

The apperance of contrainers is unlocked by OS-level virtualization and as a result, multiple application can run on the same OS. By nature, containers are lightweight, as these encapsulate only the application code and essential dependencies. Consequently, there is a better usage of available infrastructure and a more efficient pathway to release a product to consumers.

### Dockerfile
Docker is used to containerize an application. Three main components are distinguished: Dockerfiles, Dokerimages, and Doker registries. 

A __Dockerfile__ is a set of instructions used to create a Docker image. Each instruction is an operation used to package the application, such as installing dependencies, compile the code, or impersonate a specific user.

To construct a Dockerfile, it is necessary to use the pre-defined instrictions, suck as:
```
FORM - to set the base image
RUN - to execute a command
COPY & ADD - to copy files from host to the container
CMD - to set the default command to execute when the container starts
EXPOSE - to expose an application port
```

### Docker Image

A __Docker image__ is a read-only template that is used to spin up a runnable instance of an application. A docker Image provides the execution envronment for an application, including any essential code, config files, and dependencies. A Docker image can be build from an existing Dockerfile using the `docker build` command.



### Docker Registry





