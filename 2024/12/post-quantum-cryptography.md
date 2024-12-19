## Testing
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

[^1]: My reference.
[^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
This is a second line.