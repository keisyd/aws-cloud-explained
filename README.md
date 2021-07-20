# EC2

- EC2 is one of the most popular of AWS’ offering 
- EC2 = Elastic Compute Cloud = Infrastructure as a Service
- It’s not only one service, you can use:
    - Renting virtual machines (EC2)
    - Storing data on virtual drives (EBS)
    - Distributing load across machines (ELB)
    - Scaling the services using an auto-scaling group (ASG)
- Knowing EC2 is fundamental to understand how the cloud works, because cloud is all about to be able to rent these computes whenever you need and the EC2 is just that.

# EC2 Sizing & Configuration options

- Operating System (OS): Linux, Windows or Mac OS
- How much Compute power & core (CPU)
- How much storage space:
    - Network-attached (EBS & EFS)
    - hardware (EC2 Instance Store)
- Network card: speed of the card, Public IP address
- Firewall rules: security group
- Bootstrap script (configure at first launch): EC2 User Data

Basically you can choose how you want your virtual machine to be.

# EC2 User Data

- It is possible to bootstrap our instances using an EC2 User Data script
- Bootstrapping means **launching commands when a machine start**
    - That script is only run once at the instance first start and never run again 
- EC2 user data is used to automate **BOOT** (hence the name) tasks such as:
    - Installing updates
    - Installing software
    - Downloading common files from the internet
    - Anything you can think of
- The EC2 User Data Script runs with the root user

# Security Group

Let’s talk about these firewall, as the name expose, it’s to protect from fire meaning that it will block everything the comes and you can only **allow ** some traffic to work with it.

- Security Groups are the fundamental of network security in AWS
- They control how traffic is allowed into or out of our EC2 Instances
- Security groups only contain allow rules
- Security groups rules can reference by IP or by security group

So Image yourself in a computer like a cellphone trying to connect to your EC2 instance. Well, a [firewall](https://www.barracuda.com/glossary/cloud-firewall#:~:text=Cloud%20Firewalls%20are%20software%2Dbased,sit%20within%20online%20application%20environments.) will be around it blocking the access. This firewall will have rules that relate with **outbound **and **inbound **traffic. 

### Inbound

Inbound traffic is when some client ( or any computer outside your network ) tries a connection to your network, as shown in the image bellow. The firewall will block this connection by default unless you explicitly specify not to.

### Outbound

Outbound requests happens when some computer in your network requests a connection to a computer outside your network. All the requests will be authorized by default  unless you explicitly specify not to.

![](https://cdn.ttgtmedia.com/rms/onlineImages/security-inbound_outbound_firewall_mobile.jpg)
** **

# Deep Dive

- Security groups are acting as a “firewall” on EC2 instances
- They regulate:
    - Access to Ports
    - Authorized Ip ranges - IPV4 and IPV6
    - Control of inbound network (from other to the instance)
    - Control of outbound network (from the instance to other)
- They can be attached to multiple instances
- Locked down to a region /VPC combination
- Does live “outside” the EC2.
- It’s goo to maintain one separate security group for SSH access
- If your application is not accessible (time out), then it’s a security group issue
- If your application gives a “connection refused” error, then it’s an application error or it’s not launched.
- All inbound traffic is **blocked ** by default
- All outbound traffic is **authorized **by default
