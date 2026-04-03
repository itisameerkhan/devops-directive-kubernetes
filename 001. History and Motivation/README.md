# History and Motivation

## 2000s "Traditional Deployment Era"

* On premises (self-managed or colocation)
* Teams of sysadmins handle provisioning and managing fleets of servers
* Bare metal 🤘
* Monoliths are the only practical architecture
* Home grown monitoring tooling

## 2010s "Virtualized Deployment Era"

* Clouds enable VMs to be created/destroyed in minutes
* Configuration management tooling (e.g. puppet and chef)
* Manual bin-packing of apps onto VMs
* Improved tooling made managing larger number of applications practical
* Managing large numbers of cloud resources is a challenge

## 2020s "Container Deployment Era"

* Workload orchestrators enable treating clusters of machines as a single resource
* These often include utilities and standard interfaces to address:
  * Efficient scheduling across instances
  * Health checks
  * Service discovery
  * Configuration management
  * Autoscaling
  * Persistent storage
  * Networking