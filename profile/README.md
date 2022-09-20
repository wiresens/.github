# Wiresens Trading Solutions
## What
* API's, Libraries and Tools to build own low-latency Trading Platform
* Gateways Supporting Live Market Data Streaming  and Order Management
* Event logs Capturing Historical Data
* Framework for Back-Testing and Historical Simulation
## Framework / Objectives
* Open API with no lock-in (MIT license)
* Tools are free to use (with a strong motivation to open source)
* Very low-latency to support market making (single digit microsecond response time on a high-end server)
* Gateways require a license agreement (free to download and use for evaluation and development purposes)
> We do not do NDA
## Design
![architecture_v9](https://user-images.githubusercontent.com/61380379/191274730-cd287d0f-f4cc-4512-b5be-bb5112609118.png)
# Components
* Control Plane
* Worker Nodes

Worker Nodes perform effective trading. They receive instructions from the Control Plane. A worker is made of 3 main components: FeedHanler, Strategy and Execution.
The solution may be deployed in in cluster configuration with one Control plane on a separate linux machine and several worker nodes. A single node configuration is possible, with control plane and worker on same machine
## Control Plane
* API Server
* etcd
* CLI
* Ansible
### API Server
### etcd
### CLI
### Ansible
## Worker Node
They all work as daemon processes
* FeedHanler
* Strategy
* Execution
* Infrastructure Services
### FeedHanler
* Maintain network connectivity with the Binance exchange
* Route exchange updates to connected clients
* Route client requests to the relevant exchange accounts
* Stream all messages to an event-log
### Strategy
An API providing with uniform interface for communication with the gateways. Strategies should preferably be implemented using C++20. It is a Multithreaded process, with :
* StrategeyMaster, coordinating the acties of other threads
* PolicyObjects, run the strategy , sending execution orders to Excution via the Opportunity Queue.
### Execution
### Infrastructure Services
* Kafka Event-Streaming 
* systemd-journald
* PostgreSQL
