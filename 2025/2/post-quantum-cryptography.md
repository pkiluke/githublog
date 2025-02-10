<div align="center">
<img src="https://github.com/pkiluke/githublog/blob/main/2025/2/images/quantum-computer-background.jpg"/>
</div>

# Introduction
Welcome dear readers,

Today, I will introduce the foundations of [post-quantum cryptography](https://en.wikipedia.org/wiki/Post-quantum_cryptography) (hereafter referred to as PQC) and its implications to data protection. The PQC is one of the emerging technologies, by many considered to be to 2025 what AI was to 2024, that has a huge potential to impact, and by impact, I mean break, data confidentiality and data integrity.

Enjoy the reading!

# A paradigm that breaks cryptography
Quantum computing is a type of computing paradigm that utilizes the principles of quantum mechanics to process information. Quantum computers or more specifically cryptographically relevant quantum computers (hereafter referred to as CRQC), albeit still in the experimental and early development stages, have the potential to solve certain mathematical problems much faster than conventional computers.

In order to break conventional cryptography, you need a quantum computer (CRQC) with enough qubits and not only that, but with enough stable qubits. Quantum computers are extremely susceptible to thermal and electromagnetic interference (called decoherence) that results in high error rate (causing instability).

To put the security of conventional cryptography and the chaos in PQC in perspective, as of 2025, there are ~10 different technologies how to build a quantum computer, there are quantum computers with ~100-1000 qubits and in order to break RSA-2048, according to the available information you need 300 or maybe 1000 or maybe 4000 qubits.

As mentioned above, CRQC can solve certain mathematical problems much faster than conventional computers, these mathematical problems include [factoring large numbers](https://en.wikipedia.org/wiki/Integer_factorization) (RSA) and solving [discrete logarithm](https://en.wikipedia.org/wiki/Discrete_logarithm) problems (Diffie-Hellman, ECC), which form the basis for many encryption schemes currently used today.

In simple terms, the security of a cryptographic scheme (RSA, ECC, AES) is expressed as a [security level](https://en.wikipedia.org/wiki/Security_level) in bits, the security level determines how many operations the attacker has to perform to break the encryption, therefore a security level of 112 means the attacker needs to perform $2^{112}$ operations to break the encryption. Whether a single operation is adding two numbers together or something more advanced is beyond the scope of the article.

In general, the higher the security level the more secure the encryption, see below,

| Scheme | Key length [bits] | Security level<br/>(conventional computing) [bits] | Security level<br/>(quantum computing) [bits] |
|:---:|:---:|:---:|:---:|
|  RSA-2048  |  2048  |   112   |   $${\color{red}0}$$   |
|  ECC-256   |  256   |   128   |   $${\color{red}0}$$   |
|  ECC-384   |  284   |   192   |   $${\color{red}0}$$   |
|  AES-128   |  128   |   128   |   $${\color{red}64}$$  |
|  AES-256   |  256   |   256   |   $${\color{red}128}$$ |

In the context of quantum computing, there are two quantum algorithms and two categories of conventional cryptography,

- [Grover's algorithm](https://en.wikipedia.org/wiki/Grover%27s_algorithm) breaks [symmetric cryptography](https://en.wikipedia.org/wiki/Symmetric-key_algorithm)
- [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm) breaks [asymmetric cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)

As shown in the table above, the Grover's algorithm halves the security level of symmetric encryption schemes and while the more conservative security experts recommend doubling the size of the symmetric keys to remain safe from CRQC, **symmetric cryptography** is expected to remain quantum safe without doubling the key size. On the other hand, the **asymmetric cryptography** is expected to be quantum vulnerable, in other words it is expected that CRQC will break **asymmetric cryptography**.

PQC to the rescue. Here are a few definitions and challenges arising from the use of PQC,

- State-of-the-art cryptography
- Cryptographic algorithms resistant to CRQC
- Different mathematics from conventional cryptography ([code-based](https://en.wikipedia.org/wiki/McEliece_cryptosystem), [lattice-based](https://en.wikipedia.org/wiki/Lattice-based_cryptography), [multivariate](https://en.wikipedia.org/wiki/Multivariate_cryptography), [hash-based](https://en.wikipedia.org/wiki/Hash-based_cryptography))
- Developed in conventional programming languages (C, C++, Rust, Java)
- Runs on conventional computers
- Slower performance than conventional cryptography, approximately 10-20% slower
- Larger cryptographic keys and signature sizes
- Longer verification and signing times
- Larger TLS handshakes and larger data throughput.

# Navigating the migration
Many assets are at risk of compromise by the CRQC, but the risks are challenging to quantify and difficult to predict because as of February 2025 there are no known CRQC sufficiently powerful to break the conventional cryptography and no definite timelines other than “as soon as possible” or “as soon as practicable” exist. Most estimates fall within the range of 5-25 years from now.

From the perspective of risk, the risk of quantum computing is not on the CISO radar due to the fact that CISOs and other stakeholders focus on risks within a very short time horizon compared to the quantum computing timelines. For reference, the most visible areas of risk to the CISOs and other stakeholders are user awareness and data (cloud, AI).

The following lists the main guiding principles, risks and pain points influencing the migration to PQC.

- **Store-now-decrypt-later** or **harvest-now-decrypt-later** is a method of surveillance where the data protected by cryptographic controls is collected and stored until such time when a sufficiently powerful CRQC becomes available to decrypt it
- **Legacy** and **long-lived systems** - There are many challenges with **legacy** and **long-lived systems** (such as critical infrastructure or OT). **Legacy systems** suffer from obsolete hardware and software incompatible with PQC algorithms while **long-lived systems** suffer from constrained-performance (hardware not powerful enough) and difficulty, if not impossibility, to replace the hardware post-deployment
- **Complexity of cryptographic migration** - Updating or replacing cryptographic infrastructure with PQC is a complex and time-consuming activity and depending on the size of the enterprise it might take many years to finish
- **State-of-the-art** - The PQC represents the state-of-the-art in cryptography and has been adopted by governments and industries worldwide
- **No-regret moves** - Whether CRQC becomes a reality or not, many steps in the PQC migration are considered no-regret, in other words they are useful to execute either way, such as,
    - Establishing cryptographic asset management
    - Reviewing cryptographic policies & standards
    - Assessing supply chain dependencies
    - Conducting a risk assessment
    - Estimating costs of the migration
    - Assessing regulatory requirements
    - Developing a backup plan
    - Collaborating with other entities in the industry
- **Performance** and **cost** will have a major impact on the migration. As you can see in the table below, the size of cryptographic keys and signatures of PQC algorithms (ML-DSA, SLH-DSA) is many times larger than those of conventional cryptography (RSA, ECC) which will have storage and cost implications on the systems and services charged for egress traffic (such as cloud) and for devices with limited storage, the size will also have impact on network optimization and fragmentation (exceeding the size of the MTU), signing and verification operations (measured in CPU cycles) is also much larger for PQC algorithms which will have impact on performance-constrained devices such as those used in OT. However, the performance metrics (sign, verify) should be taken with a grain of salt as they are subject to optimization and further development in the PQC space.
- **Cryptographic agility** refers to the ability to adapt to risks surrounding cryptography with minimal effort, structuring technology, processes and policies such that cryptography can be used in efficient manner, cryptography can be updated, changed or completely replaced with minimal effort and minimal consequences such as a downtime.

| Scheme | Public key (pk)<br/>[bytes] | Signature (sig)<br/>[bytes] | Public key + signature<br/>[bytes] | Sign<br/>[CPU cycles] | Verify<br/>[CPU cycles] |
|:---:|:---:|:---:|:---:|:---:|:---:|
|  RSA-2048 |   272    |   256     |   528     |   27m         |   45k       |
|  EdDSA    |   64     |   64      |   96      |   42k         |   130k      |
|  ML-DSA   |   1k-2k  |   2k-4k   |   3k-7k   |   333k-642k   |   118k-279k |
|  SLH-DSA  |   32-64  |   7k-49k  |   7k-49k  |   239m-7000m  |   4m-19m    |

For more performance metrics, please check the [Post-Quantum signatures zoo](https://pqshield.github.io/nist-sigs-zoo/).

The following is the simplified version of the PQC migration (call it a roadmap).

The PQC migration comes down to three parts, the preparation, the planning and the execution

<ins>A. Preparing for the migration</ins>
- **Inventory of all cryptographic assets used in the enterprise**
    - Create an exhaustive detailed list of the use of cryptography, both hardware and software
    - Update cryptography policies & standards
    - Define a strategy for cryptographic discovery (objective, scope, methodology, reporting, review)
- **Inventory of all data assets (only a subset of data attributes)**
    - State of the data asset (data at-rest, data in-transit, data in-use)
    - Location of the data asset (physical and logical)
    - Value of the data asset (from the perspective of confidentiality, integrity and availability)
    - Classification of the data asset
    - Risk assessment for each data asset
- **Identify the dependencies in the cryptography supply-chain**
    - List cryptography hardware and software products supplied by external vendors
    - Maintain up to date vendor contact information
    - Review vendor contracts
    - Maintain communication with vendors on the progress of PQC in their respective products
- **Risk assessment**
    - Assess weakness to CRQC
    - Assess impact and determine impact score
    - Assess migration effort to PQC
    - Compute the risk score

<ins>B. Planning the migration</ins>
- **When to start the migration**
    - **Mosca's inequality**: X+Y < Z; X = how long must the data remain secure, Y = time needed to migrate to PQC, Z = when will CRQC become available; the closer X+Y is to Z the more urgent is the migration, if X+Y > Z then the data asset is already vulnerable to CRQC
- **Advice on migration planning**
    - Decide if cryptographic control must be replaced and what should it be replaced with
    - Decide order in which to migrate the data asset - confidentiality → integrity or integrity → confidentiality
- **Costs of the migration**
    - Cost estimation
    - Resource allocation

<ins>C. Executing the migration</ins>
- **Migration of symmetric cryptography**
    - No major effort is expected as symmetric cryptography is not considered vulnerable to CRQC
- **Migration of asymmetric cryptography in a hybrid deployment**
    - Hybrid deployment refers to using PQC and conventional cryptography in parallel within the same protocol
    - Mitigates the risk of undiscovered vulnerabilities in PQC, but increases the deployment complexity and attack surface
- **Migrating protocols**
    - TLS, SSH, S/MIME, PGP, IPSec, X.509

# Market trends and the current state of PQC
We might be a decade or two away from a practical CRQC, but the market moves forward every year in the PQC space. See below,

- IBM R&D has re-classified PQC from **RESEARCH** to **IMPLEMENTATION & ENGINEERING**
- In 2016, the Linux Foundation has started the [Open Quantum Safe](https://openquantumsafe.org/) open-source project and the [liboqs](https://openquantumsafe.org/liboqs/) library
- In 2022, [Google supports PQC internally in ALTS](https://cloud.google.com/blog/products/identity-security/why-google-now-uses-post-quantum-cryptography-for-internal-comms)
- In 2022, NSA has released [CNSA 2.0](https://en.wikipedia.org/wiki/Commercial_National_Security_Algorithm_Suite) mandating the use of PQC algorithms ([ML-KEM](https://csrc.nist.gov/pubs/fips/203/final), [ML-DSA](https://csrc.nist.gov/pubs/fips/204/final), [XMSS and LMS](https://csrc.nist.gov/pubs/sp/800/208/final)) to protect US national security systems by 2030
- In 2023, [Signal](https://signal.org/), a messaging protocol used in WhatsApp, has added the [PQXDH](https://signal.org/docs/specifications/pqxdh/) key exchange algorithm based on ML-KEM
- In 2024, Apple has introduced the [PQ3](https://security.apple.com/blog/imessage-pq3/) protocol based on ML-KEM to iMessage
- In 2024, [NIST releases standards for PQC algorithms](https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards), ML-KEM formerly CRYSTALS-Kyber, ML-DSA formerly CRYSTALS-Dilithium and SLH-DSA formerly Sphincs+
- In 2024, [Google develops a 105-qubit quantum chip called Willow](https://blog.google/technology/research/google-willow-quantum-chip/)
- [BouncyCastle](https://www.bouncycastle.org/documentation/specification_interoperability/#Post-Quantum-Algorithm-Support), a popular Java library supports PQC
- [PQC migration handbook](https://english.aivd.nl/publications/publications/2024/12/3/the-pqc-migration-handbook) by the General Intelligence and Security Service ([AIVD](https://english.aivd.nl/))
- Microsoft resources, [Azure PQC](https://quantum.microsoft.com/)
- Amazon resources, [AWS PQC](https://aws.amazon.com/security/post-quantum-cryptography/)
- Google resources, [GCP PQC](https://cloud.google.com/security/resources/post-quantum-cryptography?hl=en)
- IBM resources, [IBM PQC](https://www.ibm.com/quantum/quantum-safe)
- Cloudflare resources,
    - [Sizing up post-quantum signatures](https://blog.cloudflare.com/sizing-up-post-quantum-signatures/)
    - [Deep dive into a post-quantum signature scheme](https://blog.cloudflare.com/post-quantum-signatures/)
    - [The state of the post-quantum Internet](https://blog.cloudflare.com/pq-2024/)
    - [A look at the latest post-quantum signature standardization candidates](https://blog.cloudflare.com/another-look-at-pq-signatures/)

# Conclusion
Besides the advancement by companies like Google, Microsoft, Amazon, Cloudflare, IBM, there are sector-specific legislations such as,

- **Digital Operational Resilience Act (DORA)** - requires financial institutes to deploy “leading practices and standards” in cryptography
- **Health Insurance Portability and Accountability Act (HIPAA)** - mandates the healthcare industry to safeguard patient records, for instance by deploying appropriate cryptographic techniques
- **European Electronic Communications Code (EECC)** - regulates electronic communication networks in the EU and, for instance, requires the use of strong cryptography to minimize the impact of security incidents
- **Network and Information Systems (NIS)** - the successor to NIS, NIS2, does specify the obligation to deploy proportional cryptographic measures, taking into account both an organization's exposure to risks and the state-of-the-art in cryptography
- **Commercial National Security Algorithm Suite (CNSA)** - requires a specific set of cryptographic algorithms to be used for protecting US national security systems (NSS). CNSA 2.0 specifies four quantum-resistant public-key algorithms ML-KEM, ML-DSA, XMSS and LSS

there are standardization bodies such as **ISO/IEC**, **IETF**, **ETSI** developing and updating standards to mandate the use of state-of-the-art cryptography and there are governments around the world including the **EU Commission**, **Germany (BSI)**, **France (ANSSI)**, **Netherlands**, **the UK (UK-NCSC, GCHQ)**, **Czech Republic (NÚKIB)** and **USA** all pushing for the adoption of PQC.

In January 2025, the US government (Biden administration) has released the [Executive Order on Strengthening and Promoting Innovation in the Nation’s Cybersecurity](https://bidenwhitehouse.archives.gov/briefing-room/statements-releases/2025/01/15/fact-sheet-new-executive-order-on-strengthening-and-promoting-innovation-in-the-nations-cybersecurity/) that states,

> (iii)  Agencies shall implement PQC key establishment or hybrid key establishment including a PQC algorithm as soon as practicable upon support being provided by network security products and services already deployed in their network architectures.

> (iv)   Within 90 days of the date of this order, the Secretary of State and the Secretary of Commerce, acting through the Director of NIST and the Under Secretary for International Trade, shall identify and engage foreign governments and industry groups in key countries to encourage their transition to PQC algorithms standardized by NIST.the US government is saying US government agencies and their allies need to be moving to post-quantum cryptography (PQC) as soon as possible.

> (i)    Within 180 days of the date of this order, the Secretary of Homeland Security, acting through the Director of CISA, shall release and thereafter regularly update a list of product categories in which products that support post-quantum cryptography (PQC) are widely available.

In other words, the US government agencies and their allies (customers who are doing business with the US government) need to be moving to the PQC as soon as possible.

At the end of the day the only moving force is always the laws and regulations. The question is, what laws and regulations move your organization?