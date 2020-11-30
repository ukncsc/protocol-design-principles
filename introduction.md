# Introduction

Over the last twenty years, the internet has changed beyond recognition, and it will continue to change.
The number of internet users has grown massively, and the number of endpoints has grown even faster. The types of user (and the variety of devices they use to connect to the internet) are both much more diverse than twenty years ago. We’ve moved from a world of desktops talking to servers, to one where children have smartphones and a group of kitchen appliances can launch a Distributed Denial-of-Service (DDoS) attack.

This white paper defines a set of design principles for protocols, created to address these fundamental changes in internet use and the continually developing threat landscape. As threats and use cases evolve, internet protocols should too. The principles in this white paper put user needs at the heart of the design process to make sure that protocols provide functionality and security for users. This set of principles doesn’t attempt or claim to cover every aspect of protocol design, but it does cover some of the most vital issues.

These principles are aimed at the designers of protocols, to help them produce secure protocols standards and implementations that are suitable for today’s and tomorrow’s internet.  While these principles were written primarily with internet protocols in mind, they may have wider applicability and utility to any protocol designer who wants to provide users with secure protocols that meet their needs. The principles should be considered early in the protocol design process, but can also be used to review existing protocols.

## How has the internet changed?

A full examination of how the internet has changed during the last twenty years and continues to evolve is beyond this document’s scope. What follows is a non-exhaustive summary of the more substantial changes. These are:
1.	The richer multi-stakeholder environment
2.	The architectural changes as the use of Content Delivery Networks (CDNs), cloud computing and edge computing grows
3.	The massive rise in cyber attacks, threat actors and their sophistication
4.	The growth of an increasingly complex security ecosystem
5.	The increase in diversity of user and device profiles

### Multi-stakeholder environment

The internet is a rich ecosystem that is enabled by a range of stakeholders – their roles are changing, becoming increasingly important and need to be considered. Even in a relatively simple case, like an internet of Things (IoT) device in a home, there are many stakeholders:

* the owner of the data who needs their personal data to be protected
* the owner and operator of a device who wants to ensure its secure operation
* the manufacturer of the device who wants to make sure it’s not malfunctioning
* a provider of a service that the device uses, who wants to confirm they’re getting and providing all of the data they need to
* the ISP or telecommunications provider that needs to provide a reliable and performant connection
* company performing data analytics for the device manufacturer

All of these parties and more have important roles in ensuring a secure service and providing the functionality the user expects, where they didn't before. In addition, traditional roles are shifting, with more previously lower level responsibilities being undertaken at the application layer. As a consequence, some of these stakeholders may now be liable to provide aspects of the service, and hence need to ensure a good user experience for the aspects they supply. The interests of the end user are paramount [RFC8890](https://www.rfc-editor.org/rfc/rfc8890.html), and should be favoured over those of other parties, noting that for the end user to get the functionality they require, other stakeholders need to be able to perform their roles.

### Architectural changes

The architecture of the internet has changed. A big part of this is the growth in CDNs; global networks of servers that serve content on behalf of their customers. CDNs aim to provide a consistent, fast and reliable service to their customers’ users. In practice, this means that those users won’t connect directly to the server they might expect to; instead they connect to a server owned by the CDN that delivers the content on behalf of (or routes the user to) that server. The routing of large amounts of traffic is therefore controlled by CDNs, rather than chosen by the user’s ISP, representing a shift of architecture and stakeholder role.
CDNs have also driven a trend towards edge computing, where more processing is performed nearer to user devices - at the ‘edge’ of the network. In the CDN case, this means delivering content to the user from a server geographically close to them, to reduce latency. The growth in edge computing has also meant increasing geographical distribution of processing power, enabling CDNs to improve performance.

The growth of cloud computing has also been a major architectural change. This has provided convenience for everyday users, supported growing numbers of IoT devices, and encouraged a dramatic shift in enterprise IT from local to cloud-based solutions. For enterprises, cloud computing provides access to agile, convenient, robust and scalable solutions. These could be in the form of SaaS (Software As A Service) products such as multi-user messaging and video apps or IaaS (Infrastructure As A Service) products that allow enterprises to add and remove servers with ease, as they are needed. While edge computing has begun to diversify processing power geographically, increased use of cloud computing means that more and more hosting is done in large data centres owned by cloud computing services, routing traffic to a relatively small number of locations owned by a small number of providers.

### Rise in cyber attacks

Cyber attacks are increasing in scale, ingenuity, and variety. There are a range of reasons for this increase, but two key reasons are the increased opportunity for malicious actors to conduct cyber attacks and the increased impact of those attacks.

**Increased opportunity.** There are far more internet-connected endpoints than twenty years ago, and hence there are more devices that are poorly secured and vulnerable to attack. Broadly available ‘off-the-shelf’ attacker tools have increased in sophistication, number and potency. This means that it’s easy for criminals with little experience to use existing malware to conduct cyber attacks with widely felt impact. Attacker tools are widely available, reducing the bar to entry, but also encouraging waves of similar attacks as tools are incrementally changed to defeat mitigations and increase target space. Increased consumer bandwidth has augmented the power of botnets, such as [Mirai](https://blog.cloudflare.com/inside-mirai-the-infamous-iot-botnet-a-retrospective-analysis/) and its successors, to conduct massively disruptive DDOS attacks.

**Increased impact.** A breach of a single entity can affect the privacy of millions of users. Each of those users likely has accounts with many other services, so the loss of personal data or passwords can lead to further accounts being breached from otherwise secure services. It’s not only privacy, however, that is impacted by cyber attacks; the impact on availability of services can be equally significant. The world is increasingly connected – compromised industrial control systems and IoT devices can lead to physical consequences, and the compromise of internet-connected endpoints relied on by vital services can have massive effects. The [WannaCry ransomware famously impacted the UK NHS](https://www.bbc.co.uk/news/health-39899646), as vital systems were disrupted, putting patient health at risk. The large and ever increasing variety of attacks can make it hard for defenders to keep up, and the quick turnaround of attacks means new mitigations are needed all the time.

For most users, the most likely threat to their privacy online is the breach of a poorly secured system at an airline, hotel chain or social media platform - leaving an attacker with access to all of their personal details. Fixing these vulnerable systems is therefore a priority, but the security of the protocols they interact with is just as critical.

### Increasingly complex security ecosystem

Increasingly, security means more than just encryption, not least because authentication is just as important. Looking out for a padlock in your browser’s address bar gives no security if you’re communicating directly with an attacker. An attacker using a password obtained in a breach appears identical to a user accessing their account legitimately. Many devices have no way to provide even simple trust indicators to users, nor assess the legitimacy of connections. Though the burden of assessing legitimacy should not be on users, and devices should be secure by default, in practice, this is often not the case. This highlights the growing need to consider the environment the protocol is operating in – the increasingly complex ecosystem means that assumptions about security are very hard to make.

Protocols form just one part of the security ecosystem. In the same way that using an encrypted protocol to communicate with an attacker misses the bigger picture, using secure protocols that undermine security elsewhere (for example by hindering malware detection or concentrating user data in the hands of a few service providers) can be counterproductive. No protocol operates in a vacuum, and they need to support security, in the present and future, in all aspects of that ecosystem.

### Diverse users and devices

With the massive growth in user and device diversity - as well as the multiple stakeholders in even the simplest interaction - the variety in use cases for internet protocols is now vast. Advances in technology, and its affordability, mean that everyday consumers have many more internet-connected devices than they used to, from mobile phones to smart fridges. Not every protocol has the same job, not every protocol operates in the same ecosystem and not every protocol has the same user base. These are self-evident statements but, together, they lead to the conclusion that each protocol has a unique threat surface and different requirements on how it should address those threats. Some protocols have a diverse range of use cases - considering all of those use cases is important, and improvements made to support one use case could be detrimental when the protocol is used for another. 
Principles for an evolving threat landscape

Against the backdrop of these changes, trying to define an entirely new threat model to make a ‘one size fits all’ solution is not the right approach. Instead of conducting threat modelling tickbox exercises, protocol designers should develop threat models unique to each protocol, supported by a framework of key principles that every protocol designer should consider. The NCSC believes that these principles will help designers produce protocols that are not just secure against these new threats, but also meet user needs.
