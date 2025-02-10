# Introduction
Welcome dear readers,

Today, I will introduce the foundations of [post-quantum cryptography](https://en.wikipedia.org/wiki/Post-quantum_cryptography) (hereafter referred to as PQC) and its implications to data protection. The PQC is one of the emerging technologies, by many considered to be to 2025 what AI was to 2024, that has a huge potential to impact, and by impact, I mean break, data confidentiality and data integrity.

Enjoy the reading!

# A paradigm that breaks cryptography
Quantum computing is a type of computing paradigm that utilizes the principles of quantum mechanics to process information. Quantum computers or more specifically cryptographically relevant quantum computers (hereafter referred to as CRQC), albeit still in the experimental and early development stages, have the potential to solve certain mathematical problems much faster than conventional computers.

In order to break conventional cryptography, you need a quantum computer (CRQC) with enough qubits and not only that, but with enough stable qubits. Quantum computers are extremely susceptible to thermal and electromagnetic interference (called decoherence) that results in high error rate (causing instability).

To put the security of conventional cryptography and the chaos in PQC in perspective, as of 2025, there are ~10 different technologies how to build a quantum computer, there are quantum computers with ~100-1000 qubits and in order to break RSA-2048, according to the available information you need 300 or maybe 1000 or maybe 4000 qubits.

As mentioned above, CRQC can solve certain mathematical problems much faster than conventional computers, these mathematical problems include [factoring large numbers](https://en.wikipedia.org/wiki/Integer_factorization) (RSA) and solving [discrete logarithm](https://en.wikipedia.org/wiki/Discrete_logarithm) problems (Diffie-Hellman, ECC), which form the basis for many encryption schemes currently used today.

In simple terms, the security of a cryptographic scheme (RSA, ECC, AES) is expressed as a [security level](https://en.wikipedia.org/wiki/Security_level) in bits, the security level determines how many operations the attacker has to perform to break the encryption, therefore a security level of 112 means the attacker needs to perform 2112 operations to break the encryption. Whether a single operation is adding two numbers together or something more advanced is beyond the scope of the article.

In general, the higher the security level the more secure the encryption, see below,

| Scheme | Key length [bits] | Security level<br/>(conventional computing) [bits] | Security level<br/>(quantum computing) [bits] |
|:---------:|:---------------:|:--------------------------------------------------:|:--------------------------------------------------:|
|  RSA-2048  |      2048       |                        112                         |           $${\color{red}0}$$         |
|  ECC-256  |      256       |                        128                         |                        $${\color{red}0}$$            |
|    ECC-384    |     284     |                        192                         |                        $${\color{red}0}$$           |
|    AES-128    |     128     |                        128                         |                        **64**                         |
|    AES-256    |     256     |                        256                         |                        **128**                         |

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

- Quantum vulnerability diagnosis
  - inventory of cryptographic primitives and protocols
  - identify data and communication channels protected
  - conduct (quantum) risk assessment
    - is it urgent to migrate to PQC?
    - cryptographic assets managed by vendors
    - demand PQC readiness from vendors
    - establish as much of a cryptographic agility as possible when revising existing cryptographic infrastructure(s)
- Planning
- Execution

# Conclusion
[to be added]

Some basic Git commands are:
```
git status
git add
git commit
```

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

| Command | Description |
| --- | --- |
| `git status` | List all *new or modified* files |
| `git diff` | Show file differences that **haven't been** staged |

| Crypto library | Stateful DSA | Stateless DSA | KEM | Hybrid | Certification |
|----------------| --- | --- | --- | --- | --- |
| Bouncy Castle  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

| Algorithm | Key size [bits] | Security strength<br/>on classical computer [bits] |
|:---------:|:---------------:|:--------------------------------------------------:|
|  DH, RSA  |      2048       |                        112                         |
|  DH, RSA  |      3072       |                        128                         |
|    ECC    |     224-255     |                        112                         |
|    ECC    |     256-383     |                        128                         |
|    ECC    |     384-511     |                        192                         |
| ECC |   $\geq$ 512    | 256 |
| AES |       128       |                        128                         |
| AES |       256       |                        256                         |

```python
def add_round(s, k):
    # state2 = sum(s, [])
    # key2 = sum(k, [])
    return [[sss ^ kkk for sss, kkk in zip(ss, kk)] for ss, kk in zip(s, k)]
```

Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

This is a link to [Google website](https://www.google.com)

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].

pewpew a lot of text

This sentence uses `$` and `$` delimiters to show math inline: $`\sqrt{3x-1}+(1+x)^2`$

**The Cauchy-Schwarz Inequality**
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

<details>

<summary>Tips for collapsed sections</summary>

### You can add a header

You can add text within a collapsed section.

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>

**ahoj**
*ahoj*
~~ahoj~~
_ahoj_
__ahoj__
A<sub>c</sub>
A<sup>c</sup>
<ins>ahoj</ins>

> Tohle je kvotace
 
# Example 1
## Example 2
### Example 3

Link to [Example 1 section](#example-1)

Link to [Testing section](#testing)

1. First list item
    - First nested list item
        - Second nested list item

- [ ] task item #1
- [ ] task item #2
- [x] completed task item

[^1]: My reference.
[^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
This is a second line.