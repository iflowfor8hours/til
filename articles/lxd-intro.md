## Introduction to LXD — A Container-Based Hypervisor

Application Containers Vs System Containers

Linux Container Daemon, or LXD, is a new type of hypervisor from Canonical Inc, built on the same core technology as Docker but with a very different philosophy towards packaging and deployment of systems and applications.

Docker and LXD both rely on LXC and cgroups, but utilize them in very different ways to achieve different goals.

The goals of the LXD project are to allow organizations that are familiar with VMs and hypervisors to move to container-based infrastructure quickly and cleanly, without the need to rearchitect their stack to fit the containerized mindset. This is a vastly different goal than Docker. Best practices for Docker state that only a single process should run in a single container and applications deployed with it should generally follow (12 factor principles)[https://12factor.net/]. This often leads to organizations needing to change their applications to fit the assumptions of the platform.

LXD serves as a replacement for traditional hypervisors, but with the added benefits of containers such as fast startup and teardown, higher density, with the ability to utilize your existing operational tools and practices. It is built to compete with traditional hypervisors like VMWare ESX and KVM.

Why LXD?

The biggest potential benefit of LXD for many organisations is that it combines the speed of containers with the security and familiarity of more traditional virtual machines. Rather than paying the overhead of starting a virtual machine, in order to launch a guest operating system, you can do it inside LXD, using public images if desired.

Live migration is another benefit that LXD offers. The platforms supports the movement of running containers between hosts without having to shut them down each time they’re moved.

LXD also offers dynamic resource restrictions. These are helpful for assuring security and efficiency, since they prevent a single container from hogging a lot of resources and compromising the stability of other containers.

The Gears That Run LXD
LXD is essentially composed of three main components:

A system-wide daemon (lxd)
A command-line client (lxc)
An OpenStack Nova plugin (nova-compute-lxd)

These components provide different capabilities and features that make it unique, and provide advantages over traditional hypervisors. Let’s take a closer look at them and what they’re made of. 

A System-wide Daemon - LXD
At its core, LXD is a REST API for the LXC library, allowing management of containers over a network and providing communication between the client and the daemon. This also explains the difference between LXD and LXC, something that can be confusing. LXC is a simpler container experience in comparison to LXD, which expands on the solutions provided by LXC and makes them available via an API. 

A Command-Line Client (lxc)
LXC (or Linux Containers) is essentially a virtualisation system that runs containers on a single Linux host. It provides a user interface from which containers can be launched. Its code was used to develop Docker and CoreOS. LXD is an extension of LXC, using much of its code. One major difference between LXC and Docker is that Docker is used to mostly run single processes, whereas LXC runs multiple processes.

Nova-lxd - A Plugin for OpenStack
If you’re using OpenStack, you’ll be happy to know that the OpenStack APIs allow LXD integration. Nova-lxd is an OpenStack plugin that launches LXD containers in a similar way to virtual machines to allow larger deployments which LXD cannot do by itself. This allows for very large deployments of LXD on a large number of hosts, using the OpenStack APIs to manage network, storage and load-balancing. 

Now that we know what LXD is made of, let’s look at what you need to know if you are considering using LXD. 

Publishable Images
LXD creates containers from Linux distribution images, which are publishable. LXD comes pre-configured with three remote image servers:

'ubuntu,' which provides Ubuntu images
'ubuntu-daily,' which provides daily builds of Ubuntu
'images,:' a community-run image server that provides images for other Linux distributions that employ LXC templates

Security - Adopted from LXC
Security for LXD is provided by a set of features that are adopted from the LXC library. Kernel namespaces provide separation of the container from the host system; Seccomp prevents dangerous system calls from occurring; AppArmor restricts cross-container communication; Capabilities prevents containers from loading kernel modules; CGroups provides resource limitations and prevents DDoS attacks.   

Compatibility - For Now, Linux Only
At the moment, LXD is only compatible with Linux. If you don’t mind this limitation or prefer using Ubuntu or another Linux based system, then this wouldn’t be a deterrent for using it.

Conclusion

LXD is not just another container technology. It provides firm security at the speed of containers. Though still in relatively early stages of development (the first stable LXD release appeared last spring) LXD can’t be ignored. It solves a lot of shortcomings that have plagued traditional virtual machines, and it lets you run Docker containers securely and at scale. 
