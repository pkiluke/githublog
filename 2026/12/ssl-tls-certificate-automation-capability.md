# Architecture explained - SSL/TLS certificate automation
## Introduction
Welcome dear readers,

Today, I will talk about digital certificates or more specifically the SSL/TLS digital certificates and their corresponding automation capability in XYZ. 

Why should XYZ care about certificate automation? Because the most immediate reason for certificate automation are drastic certificate lifetime changes of public SSL/TLS certificates (i.e., scheduled in 2026, 2027, 2029; read more below). The other reasons are the growth of machine identities for IoT/Edge and containerized services, closing the “expired certificate” gap, avoiding the cost of failure resulting from regulatory fines and cryptographic agility.

For the more technical readers, please keep in mind that I am simplifying a lot of the contents so that the article is understandable to a broader audience.

Enjoy the reading!

## Setting the stage for XYZ
If you are XYZ application manager and you want to request SSL/TLS certificate for a business application, you should understand the following terminology.

 

Digital certificate - a logical container in the form of a file containing a cryptographic key and the associated identity metadata (e.g., device, user)

SSL/TLS digital certificate - a digital certificate issued to SSL/TLS endpoint (e.g., https://www.xyz.com)

Certificate lifetime - the time how long a digital certificate is considered valid (e.g., 1 day, 2 months, 3 years)

SSL/TLS - a method of protecting digital communication by SSL/TLS certificates between a client and a server (e.g., https://www.xyz.com)

PKI (Public Key Infrastructure) - the core infrastructure responsible for managing digital certificates

CA (Certificate Authority) - the component of PKI that creates (issues, provisions) digital certificates

CLM (Certificate lifecycle management) - the component of PKI that enables certificate automation

Certificate automation - a capability that reduces the risk of human error by automating certificate lifecycle activities (e.g., issuance, renewal, revocation)

ACME (Automated Certificate Management Environment) - a protocol that allows automation of SSL/TLS certificate lifecycle activities (e.g., issuance, renewal, revocation)

## The road to certificate automation in XYZ
As more and more XYZ business applications provide its services online (i.e., deployed in the cloud and at scale, use API for automation and communication) so too are its data and customers secured by digital certificates.

 

An expired SSL/TLS certificate is a preventable business outage

 

An expired SSL/TLS certificate causes the XYZ business application to fail, which means it either “fails closed” = application stops working or “fails open” = application exposes customer and business data. That's why an expired SSL/TLS certificate represents a risk to uninterrupted business operations and that's where certificate automation comes into play to prevent business outage.

 

When we discuss certificate automation, we must mention cryptographic agility because these two concepts are connected. You can think of certificate automation as an engine and cryptographic agility as the steering wheel, the engine provides the power to stay on the road, and the steering wheel provides direction and the ability to adapt to the road ahead.

Cryptographic agility refers to the capability of a system to change cryptographic controls (it is a way of risk mitigation) without disrupting business operations. It is a modern architecture requirement.

When we talk about cryptographic agility as connected to certificate automation, does certificate automation and therefore the frequent renewal of SSL/TLS certificate increase its security?

 

A digital certificate is a logical container in the form of a file containing

a cryptographic key and the associated identity metadata

 

The answer is yes, but... It does if the renewal is done correctly and in order for the renewal of the SSL/TLS certificate to increase security or at the very least to maintain the same level of security, the certificate has to be re-keyed upon renewal which means changing the cryptographic key in the certificate without changing the identity metadata in it.

For XYZ there are two major important changes impacting SSL/TLS certificates that XYZ application managers should pay attention to,

PQC (Post-quantum cryptography) - for more information on the topic, please read Architecture explained: Post-quantum cryptography in XYZ and follow INFOSEC: Cryptographic Controls Standard as a guidance on what cryptographic controls are allowed for XYZ SSL/TLS certificates

Certificate lifetime changes - According to CA/Browser Forum starting in March 2026, the lifetime of public SSL/TLS will be 200 days, by 2027 the lifetime will be 100 days and by 2029 only 47 days. In light of these of drastic changes, manual renewal of public SSL/TLS certificates at scale is not possible in XYZ


CA/Browser Forum scheduled certificate validity changes
If you are concerned with the decreasing certificate lifetime, let's explain what options XYZ offers and which of these options are affected by these changes,

 

Option #1 - DigiCert - DigiCert is a public trust CA, it means that,

it must follow the CA/Browser Forum, a governing body that manages the ecosystem of public trust, defines its rules (bylaws) and enforces them; members are Google, Microsoft, Mozilla, DigiCert, GlobalSign, Cisco, Apple and others

XYZ MUST follow the rules and decisions of the CA/Browser Forum

certificates created by DigiCert are trusted by operating systems and browsers by default

certificates created by DigiCert ARE IMPACTED by the changes to the certificate validity

What does it mean for XYZ? Let's describe a hypothetical example, XYZ buys SSL/TLS certificate on 1.1.2026 with a validity of 365 days from DigiCert and installs it at https://www.xyz.com. Under normal circumstances if the SSL/TLS certificate is renewed before 1.1.2027 (before the expiration date), even if it is done manually without certificate automation, the operational risk associated with changing the old certificate for a new one is small.

Why? Simply because the certificate must only be renewed once in 365 days.

Now, the CA/Browser Forum decides that SSL/TLS certificates issued on and after 1.1.2027 will have a validity of 200 days instead of 365 days.

What does it mean for XYZ? It means that the operational risk of manual renewal for https://www.xyz.com is now two times higher, because XYZ must renew the certificate twice a year instead of once a year.

What's the impact of an expired certificate? That is a question that every application manager must answer for themselves together with XYZ business based on the business criticality of the application in question and the sensitivity of the data the application receives or creates.

 

Option #2 - XYZ PKI - XYZ PKI is a private trust CA, it means that

it is only regulated by internal XYZ policies and standards; INFOSEC: Cryptographic Controls Standard

it is not trusted by operating systems and browsers by default

XYZ must install “trust” into software and hardware before use

certificates created by XYZ PKI ARE NOT IMPACTED by the changes to the certificate validity

XYZ PKI can also create SSL/TLS certificates, but because XYZ PKI is not regulated by the CA/Browser Forum it can define its own certificate lifetime and other parameters.

## The building blocks of automation in XYZ
If you are XYZ application manager and want to move from manual renewal to automatic renewal of SSL/TLS certificate, pay attention. The automation of SSL/TLS certificates in XYZ is achieved by the ACME protocol.

 

Let's use the scenarios of Infrastructure as a Service and Software as a Service for comparison to demonstrate ACME certificate automation,

 

Scenario #1 - XYZ Infrastructure as a Service - The following reference architecture shows the components and processes involved in SSL/TLS certificate deployment. From the point of view of XYZ application manager, the most important is the following,

SSL/TLS certificate #1 (edge certificate - red icon - [3])

request (9) SNOW: WAF (Akamai) - On-board Application

the certificate automation then happens between Akamai and DigiCert (3-d-7) transparently on behalf of the XYZ application manager, there is no need to do anything else by the XYZ application manager

 

SSL/TLS certificate #2 (origin certificate - blue icon [6]) - ACME automation

request (9) SNOW: ACME - Internal XYZ SSL or SNOW: ACME - External DigiCert SSL

deploy ACME (6) by following XYZ PKI team's documentation - ACME integration with XYZ PKI or ACME integration with DigiCert


Reference architecture - SSL/TLS certificate automation for Infrastructure as a Service
To summarize, for XYZ Infrastructure as a Service scenario, the entire process is semi-automated, the XYZ application manager must request ACME credentials in SNOW (9), which is a manual process, and then configure the certificate automation using ACME protocol and the ACME credentials (6).

--

--

Scenario #2 - XYZ Software as a Service - The following reference architecture shows the components and processes involved in SSL/TLS certificate deployment. From the point of view of XYZ application manager, the most important is the following,

SSL/TLS certificate (red icon [1])

XYZ application manager creates a certificate request in the SaaS platform (1)

XYZ application manager requests (2) SNOW: Internal XYZ SSL and submits the certificate request

XYZ application manager receives the SSL/TLS certificate from XYZ PKI helpdesk (3) and installs it in the SaaS platform (1)

Reference architecture - SSL/TLS certificate automation for Software as a Service
To summarize, for XYZ Software as a Service, there is no certificate automation.

For high-resolution reference architecture designs - SSL/TLS certificate automation.

## Conclusion
The certificate automation is the cornerstone of modern cryptographic agility. With post-quantum cryptography and constantly changing certificate lifetimes, the ability to rotate identities at scale is of strategic importance. Not only does the certificate automation reduce the operational risk of a human error, but it reclaims hours and hours of incident response and allows XYZ PKI team to focus their limited resources in other areas.

Additionally, automating the certificate lifecycle moves XYZ from a reactive security posture to a proactive one. By centralizing certificate visibility and removing the human factor, XYZ can ensure that cryptographic policies and standards are enforced in real-time across the ever-growing infrastructure.