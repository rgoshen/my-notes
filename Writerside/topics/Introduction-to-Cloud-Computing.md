# Introduction to Cloud Computing

## What is the Cloud? {collapsible="true" default-state="expanded"}

- means storing data and accessing computers over the internet
- it is not just storage, it'd compute, it's artificial intelligence, machine learning, etc.
- it's a bunch of different types of computing or services, and just being done on somebody else's server

## What are the Origins of the Could? {collapsible="true" default-state="expanded"}

- '60s to the original ARPANET project when they were building and architecting the internet
    - cloud symbol was used on their flowcharts
    - the idea being there that any computer that's connected to the internet has access to that pool of computing power
      and
      data
- late 1980s or early 1990s, the way people would install software on their computer was using floppy disks
- a good analogy here is like electricity for cloud computing
    - you can generate your own electricity
        - you could buy a generator
        - you could run it in your house
        - relatively expensive investment up front
            - got to buy that hardware
            - got to keep it running
            - got ongoing maintenance of your generator
    - if there are enough people around you all wanting access to electricity, it kind of makes sense to share that
      generation with everyone else
    - outsource the setup and running of the generation of electricity to someone else like the electric company
    - then anyone who needs electricity around you can just tap into it on demand, and they can just pay for what they
      use
    - it allows the energy company to focus on delivering energy, producing energy in a really efficient, fast way and
      build economies of scale
    - it allows the consumer of the energy to focus on consuming the energy to do what they want to do instead

## Who are the Different Cloud Vendors? {collapsible="true" default-state="expanded"}

- Amazon, by far the biggest
    - make up around 90% of the public cloud compute
- followed closely by Microsoft Azure
    - actually make up the next 5%
- final 5% roughly is Google, IBM, Alibaba, etc
    - Google is exceptional at big data analysis and machine learning, deep learning, and artificial intelligence

## How Did the Cloud Come About? {collapsible="true" default-state="expanded"}

- early days of the internet
    - if you wanted a server, you needed to run it yourself.
      You needed to buy one, you needed to set it up, power it up, plug it in, connect it to the internet, and you
      needed to keep it running, 24/7, keep your internet connection on
- people realized they could outsource this
    - data centers came along in a huge way
        - you could go to a data center, and they would set up racks of servers
          that you could rent for them
        - at first, they provided only infrastructure support, so they basically would provide those servers with power,
          with heating or cooling, electricity, that sort of thing, but then later on, people were requesting for
          Rackspace to support the operating systems, or to support the application layer
            - still large upfront investments
                - pay for those servers, you had to sign lengthy contracts with the data centers
- about 2006 and Amazon comes out and launches their first cloud platform, they launched EC2
    - the benefit of it was that you didn't have to worry about providing electricity, you didn't have to worry about
      providing the internet, they managed all that for you, the physical security
- the journey to cloud has really been occurring over from '95 through to about 2006

## What's a Server? {collapsible="true" default-state="expanded"}

- just like a powerful computer that you're able to access
- typically rack-mounted or put into blade chassis
- won't have a monitor that you can connect to
- connect into them remotely

## What is Serverless? {collapsible="true" default-state="expanded"}

- the cloud provider like Amazon manages all the infrastructure for you
- with serverless is give my code to Amazon or to Microsoft or to Google
    - run it whenever a customer needs something
- they deal with the challenge of scaling that
- they deal with all the operations of having people available 24/7 to fix things when things break
- they provide guarantees to me as a customer, SLAs, and I can trust them to run my code

## What is LAAS? {collapsible="true" default-state="expanded"}

- Infrastructure as a Service (IAAS) is where you have a hypervisor,
  and the hypervisor you can provision virtual machines
- it could also be where you're actually renting the physical server itself
- essentially it allows you to host an operating system in the cloud,
  which then is unique to you
    - nobody else can log into it, and you go in and then manage it yourself
- you only pay for what you use, so it depends on the model and the idea is there's no long-term or fixed contract
    - Amazon:
        - it's a per second billing model right now for Linux instances
        - windows instances are on a per-hour basis
    - Google:
        - a per minute basis

## What is PAAS? {collapsible="true" default-state="expanded"}

- Platform as a Service (PAAS) is basically something like Elastic Beanstalk
    - don't necessarily know what resources you need, but you've just got your code, and you will then use PAAS to go in
      and provision those resources for you
        - Elastic Beanstalk will provision you with elastic load balances,
          with EC2 instances, with databases, etc.
    - you still have to look after the underlying assets, but you don't have to worry about the provisioning of it

## What is SAAS? {collapsible="true" default-state="expanded"}

- Software as a Service (SAAS) is something like Gmail
- With Gmail, all you worry about is the actual software
    - worry about your inbox
    - worry about spam filters
    - not worried about the underlying servers
    - don't have to worry about how they load balance it
    - don't have to worry about how they provide high availability
    - don't have to worry how they do their DNS reading

## What is FAAS? {collapsible="true" default-state="expanded"}

- Functions as a Service (FAAS) is somebody else goes out and writes a function, which you can then use
    - you can break down your application from these monolithic applications into something that's a lot smaller and
      decoupled

Ex:

- somebody has written a function where you just take a payment
- you would then use that code and recycle that code in your own application

## What Advantages Are There Using the Cloud? {collapsible="true" default-state="expanded"}

- things like big data and analytics require an awful lot of computed power and also an awful lot of servers, especially
  if you're scaling out horizontally
    - if you were to do this yourself, you'd have to go out and buy these servers, you'd have to rack and stack them,
      power them up, and then you'd have to go through and manage them
    - if you're buying from HP or Dell, you're in three- to five-year contracts, so it's going to be very, very
      expensive
- you pay by the minute or by the hour, depending on the service, and you can go in, do your big data calculations or
  analytics, and as soon as you're finished, you can stop
- not locked in to a three- to five-year contract

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
