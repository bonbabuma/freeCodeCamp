---
title: Containers
localeTitle: 集装箱
---
## 集装箱

容器是解决从一个计算环境移动到另一个计算环境时如何使软件可靠运行的问题的解决方案。这可以是从开发人员的笔记本电脑到测试环境，从登台环境到生产，也可能是从物理机器到私有云或公共云中的虚拟机的数据中心。

换句话说，Container包含整个运行时环境：应用程序及其所有依赖项，库和其他二进制文件，以及运行它所需的配置文件，捆绑到一个包中。通过容纳应用程序平台及其依赖关系，操作系统分发和底层基础架构的差异被抽象掉了。

容器是操作系统级虚拟化 - 一种操作系统功能，其中内核允许存在多个隔离的用户空间实例。从其中运行的程序的角度来看，这种称为容器的实例可能看起来像真正的计算机。

## 虚拟机

VM本质上是对真实计算机的仿真，该计算机执行类似于真实计算机的程序。 VM使用“管理程序”在物理机器上运行。反过来，管理程序可以在主机上运行，​​也可以在“裸机”上运行。

_虚拟机管理程序_是虚拟机运行的软件，固件或硬件。管理程序本身在物理计算机上运行，​​称为“主机”。主机为VM提供资源，包括RAM和CPU。这些资源在VM之间划分，可以根据需要进行分发。因此，如果一个VM运行的资源更多的应用程序，您可能会分配更多的资源，而不是在同一主机上运行的其他VM。

在主机上运行的VM（同样，使用管理程序）通常也称为“客户机”。此客户机包含应用程序以及运行该应用程序所需的任何内容（例如系统二进制文件和库）。它还带有自己的整个虚拟化硬件堆栈，包括虚拟化网络适配器，存储和CPU - 这意味着它还拥有自己的完整客户操作系统。从内部来看，客户机具有自己的专用资源。从外部来看，我们知道它是一个VM - 共享主机提供的资源。

如上所述，来宾计算机可以在托管虚拟机管理程序或裸机虚拟机管理程序上运行。它们之间存在一些重要的差异。

首先，托管虚拟化管理程序在主机的操作系统上运行。例如，运行OSX的计算机可以在该OS之上安装VM（例如VirtualBox或VMware Workstation 8）。 VM无法直接访问硬件，因此必须通过主机操作系统（在我们的例子中是Mac的OSX）。

托管虚拟机管理程序的好处是底层硬件不那么重要。主机的操作系统负责硬件驱动程序而不是管理程序本身，因此被认为具有更多的“硬件兼容性”。另一方面，硬件和管理程序之间的这个附加层会产生更多的资源开销，从而降低VM的性能。

裸机虚拟机管理程序环境通过在主机的硬件上安装和运行来解决性能问题。因为它直接与底层硬件接口，所以它不需要运行主机操作系统。在这种情况下，作为操作系统安装在主机服务器上的第一件事就是管理程序。与托管虚拟机管理程序不同，裸机虚拟机管理程序具有自己的设备驱动程序，可直接与每个组件交互，以执行任何I / O，处理或特定于操作系统的任务。这样可以获得更好的性能，可伸缩性和稳定性。这里的权衡是硬件兼容性有限，因为管理程序只能内置如此多的设备驱动程序。

在讨论了虚拟机管理程序之后，您可能想知道为什么我们在VM和主机之间需要这个额外的“虚拟机管理程序”层。

好吧，由于VM拥有自己的虚拟操作系统，因此虚拟机管理程序在为VM提供管理和执行此客户机操作系统的平台方面发挥着重要作用。它允许主机在作为客户端运行的虚拟机之间共享其资源。

## 容器

与提供硬件虚拟化的VM不同，容器通过抽象“用户空间”来提供操作系统级虚拟化。当我们解开术语容器时，你会明白我的意思。

出于所有意图和目的，容器看起来像VM。例如，它们具有用于处理的私有空间，可以以root身份执行命令，具有专用网络接口和IP地址，允许自定义路由和iptable规则，可以挂载文件系统等。

容器和VM之间的一个重要区别是容器与其他容器_共享_主机系统的内核。

## 管弦乐编曲

生产中有几个容器编排框架：docker-swarm和kubernetes

## 容器提供商列表

Bellow是可以使用的最常用容器供应商的小清单。

*   [搬运工人](https://www.docker.com/)
*   [Kubernetes](https://kubernetes.io/)
*   [亚马逊AWS ECS](https://aws.amazon.com/ecs/?nc1=h_ls)
*   [RKT](https://github.com/rkt/rkt)
*   [Azure Fabric](https://azure.microsoft.com/en-us/services/service-fabric/)