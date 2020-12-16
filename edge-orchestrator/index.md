# Edge **Orchestrator**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/edge-orchestrator/index.md)

Azion Edge Orchestrator is an end-to-end encrypted orchestration service with cloud management and zero-touch provisioning, created for large-scale Edge networks. It allows you to manage and control Edge resources in real time, including provisioning, updating and managing Edge Applications, Edge Firewalls, Edge Functions, Digital Certificates, Edge Nodes, Edge Services and third party services (via Marketplace).

It was designed to operate and run on different types of architecture such as microprocessors, like x86 and ARM, and different sizes of equipment, including Raspberry PI, network equipment such as switches and SD-WAN routers, as well as corporate servers.

Edge Orchestrator can be used with most network architecture, including local and public networks, and also behind NATs. It is compiled with all required libraries and core dependencies, making software installation and updating simpler.

> 1. [How does it works?](#how-it-works)
> 2. [Edge Orchestrator modules](#modules)
> 3. [Supporting documentation](#support-documentation)

---

## 1. How does it work? {#how-it-works}

An Azion Edge Orchestrator agent is installed on the edge nodes and provides end-to-end encrypted remote node management from the control panel ([Real-Time Manager](https://manager.azion.com/)) based in the cloud and API. It can be deployed in two different ways: 1) through manual installation on each edge node; or 2) automatic installation along with the operating system (for example: a Linux distro or the image of a client's OS) or hardware supplier (for example: an SD-WAN router, a network switch or a Linux server). Customers can use an automatic registration mode, which makes it simpler to deploy (e.g. to new node locations or using automatic node scaling), update and manage a large number of scaling edge nodes.

All services linked to edge nodes are orchestrated and configured from the moment the device is authorized via the control panel. The orchestration is carried out sequentially, depending on the dependencies between resources and the triggers specified for your configuration.

---

## 2. Edge Orchestrator modules {#modules}

Azion Edge Orchestrator has the following modules so that you can build a high performance, scalable and secure Edge network, more simply and free from operational tasks.

### Edge Node

The Edge Node module enables devices to be created and managed, as well as integrated with Azion. You need to install our agent so that we can orchestrate its settings and ensure secure communication between the devices and Azion. [Learn more](https://www.azion.com/en/documentation/products/edge-orchestrator/edge-node)

---

### Edge Services

The Edge Services module enables the customer to create their own services. You can use your customized services with Edge and ensure your device is managed and orchestrated by Real-Time Manager.[Learn more](https://www.azion.com/en/documentation/products/edge-orchestrator/edge-services)

---

## 3. Supporting Documentation {#support-documentation}

- [Edge Node](https://www.azion.com/en/documentation/products/edge-orchestrator/edge-node)
- [Edge Services](https://www.azion.com/en/documentation/products/edge-orchestrator/edge-services)

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
