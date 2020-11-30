# Motivation for the principles

In 2019, the NCSC published its [Secure design principles for designers of secure systems](https://www.ncsc.gov.uk/collection/cyber-security-design-principles). That guidance, summarised below, provides the motivation for the protocol design principles described in the following section. By considering the three principles defined later in this document, protocol designers will be able to deliver towards each of the following five goals.

## Establish the context

Each protocol will be used differently, by different users and for different purposes. It’s important to take users, use cases, risks and threats into account when designing the protocol. Consider the unique threat model of the protocol, defining that threat model clearly, and ensuring that the protocol addresses the most important identified threats. It’s also important to identify those threats which aren’t addressed to allow users to take them into account when deploying the protocol.

## Make compromise difficult

This goal protects against data compromise through unauthorised violation of data confidentiality, data integrity or data authenticity. A large part of this is communications security, which is obviously key to secure protocol design, and more generally protecting the privacy of users by keeping personal information secure. The different types of compromise that could be made difficult are determined by the context of the protocol, with decisions driven by how to minimise the attack surface most effectively. Preventing some methods of compromise can increase the vulnerability of the system to other methods, so it is vital to take the protocol’s whole threat model into account, considering the impact of design decisions on use cases and the ability to protect against other threats.

## Make disruption difficult

Considering how best to deal with both malicious attempts to disrupt (like a DDoS attack) and non-malicious disruption (such as a server failing) are important aspects of secure protocol design. This goal is even more important for the many protocols used in critical contexts where disruption (which could be gaps in communication, high latency or unreliable service) cannot be tolerated.

## Make detecting compromises easier

At some point, an endpoint or application will be compromised. Protocols should facilitate detection of an intrusion and not aim to prevent such detection, either during or after the event. Protocol designs should consider how the protocol may be misused when an endpoint is compromised, and how that misuse could be detected, for example by exfiltration of stolen data. Compromise of an endpoint may also mean any security mechanisms it has are compromised, and could become attack vectors themselves. Though security methods are evolving, relying on host-based security alone has limitations and is not always an option, so mechanisms which allow non-endpoint components to detect and thwart compromise should be considered. This is particularly important when designing for environments such as IoT, where devices may have only limited or no host-based security.

Similarly, when profiling past malicious behaviour to detect future compromise, it is important that the user (and appropriate admins) are able to analyse what has happened to their own equipment and their own data in a way that preserves user privacy; protocols should enable this analysis to be performed. If a protocol hides this kind of information, then defenders may have to rely on logs held on a compromised endpoint (or may have no logs at all).

## Reduce the impact of compromise

Once a compromise has been detected, the user (or their network administrator, service provider or other stakeholder) needs to be able to reduce its impact. This includes minimising the amount of data an attacker can access or exfiltrate, minimising an attacker’s impact and use of data, pre-emptive action to minimise the scope of any future compromise, minimising the impact on service availability and taking active measures to protect users. Limiting an attacker’s access to data is a key consideration, for example by using short-lived credentials to reduce the window during which an attacker can exploit those credentials if compromised. Designing protocols so that data exfiltration or command and control communications can be blocked and signatured is not necessarily an easy problem, especially while protecting the content of communications, but is nonetheless vital to reduce impact. 
