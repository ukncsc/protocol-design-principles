# Summary

## Secure protocols that work for users
We think that user needs should be at the heart of protocol design – this means meeting their use cases and ensuring that solutions work for all stakeholders. These three principles – prioritise the use case, keep it simple, think about the bigger picture – will help to ensure that protocol designs provide the security users need and address the challenges of an evolving internet.

**Prioritise the use case.** First consider the context of the protocol, where it will run and what threats it will face. Within that context, make design decisions that best improve users’ security for the use case. The diversity of users’ needs, devices and environment, needs to be considered alongside support for multiple stakeholders. Levels of trust vary, the need for availability can be particularly important, and the threat surface differs by use case. Think about what you reveal and think about what you trust. Consider detection of misuse and consider resilience to both attack and failure. Enable defence-in-depth.

**Keep it simple.** Designing for simplicity leaves less space for implementation error and user error, reducing the opportunities for compromise. Making it easy for users to make secure choices, and to stay secure, has a huge impact. Avoid design complexity and make it easy to use the protocol securely. Don’t reinvent the wheel, and design for easy maintenance – which will vary, dependent on the use case prioritised.

**Think about the bigger picture.** The security of a protocol is more than just a mathematical analysis; the system it operates in, and the impact it has on the wider environment are at least as important. Encourage diversity and think about secure implementation. Allow the use of least privilege and plan for failure of third parties. Support evolution with your protocols – and help to build a secure internet ecosystem for all users. 

## Using the three principles

### Who are these principles for?

These principles are primarily aimed at designers of protocols, as a guide for use in the design process. They can also be used when implementing and deploying systems, by those who are deciding whether to use an existing protocol. Generally, the principles provide a framework with which to assess whether a protocol is both suitable and secure for a particular use case. While these principles were written primarily with internet protocols in mind, they may have wider applicability and utility to any protocol designer who wants to provide users with secure protocols.

Users and stakeholders should be front and centre in the protocol design process, and we believe these principles will help achieve that. These principles provide a vocabulary for protocol and system designers, administrators and many other stakeholders to evaluate protocols, to get involved in ongoing conversations around protocol design and to ensure their needs are met.

### How should these principles be used?

A key first part of protocol design is taking the time to establish what the use cases are for the protocol and who its users will be. From there, it is important to consider the specific threat model that the protocol will face; achieving good security isn’t possible without first understanding the threats that need to be mitigated. These principles provide a systematic but flexible guide to allow protocol designers to:
1.	**Prioritise the use case** – by considering the context around the protocol.
2.	**Keep it simple** – use this contextual understanding to keep the design simple.
3.	**Think about the bigger picture** – make relevant protocol design decisions.

These are principles, not directives. Under every principle are a few prompts and explanatory text that protocol designers should read and consider. Not every prompt will be relevant to every protocol and use case, but they should all be considered. They are all important topics, and if a protocol does not meet any of them then it should be a conscious and thought-through decision by the designer. Further, the impacts of that decision should be outlined to users, implementers and deployers.
