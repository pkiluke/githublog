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