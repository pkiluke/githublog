# Introduction
Welcome dear readers,

Cryptography is the mathematical method of protecting confidentiality and integrity of data that’s been deeply embedded
into the world’s digital society at large since 1970s. For over 50 years RSA, ECC and DH have been at the pinnacle of
commercial cryptography based on mathematical problems considered intractable by the computational resources at the
time.
In 1980s and 1990s scientists and academics started proposing combining computer science (classical computers, bits) and
quantum mechanics (quantum computers, qubits).
In and around the late 2010s the industry and academy started pursuing the engineering efforts of PQC (Post-Quantum
Cryptography) in slowly developing and standardizing algorithms to resist the quantum computers.
Today, we will talk about post-quantum cryptography, what it is and what challenges it brings.

Enjoy the reading!

# The contents
[to be added]
Let's start with a simple explanation of the "quantum" terms.

Quantum computing

Quantum computing is a type of computing paradigm that utilizes the principles of quantum mechanics to process
information. Quantum computers, which are still in the experimental and early development stages, have the potential to
solve certain mathematical problems much faster than classical computers.
These mathematical problems include integer factorization which forms the basis for RSA and discrete logarithm problem
which forms the basis for ECC (Elliptic Curve Cryptography) and DH (Diffie-Hellman)

Some of these problems include factoring large integers and solving discrete logarithm problems, which are the basis for
many commonly used encryption schemes, respectively RSA and ECC. The concern with quantum computers is that they could
break many of the encryption methods currently in use, making data and communication vulnerable to eavesdropping and
unauthorized access.

Post-Quantum Cryptography (PQC) is a new generation of cryptographic algorithms and techniques designed to resist
attacks from quantum computers.

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

|         Algorithm          |  Key size [bits]  | Security strength [bits]<br/>on classical computer |
|:--------------------------:|:-----------------:|:--------------------------------------------------:|
|  Diffie-Hellman (DH), RSA  |       2048        |                        112                         |
|  Diffie-Hellman (DH), RSA  |       3072        |                        128                         |
|            ECC             |      224-255      |                        112                         |
|            ECC             |      256-383      |                        128                         |
|            ECC             |      384-511      |                        192                         |

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