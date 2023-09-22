# Schlockchain Homepage

Welcome to the future.

The logo is at {ref}`the Python logo <logo-target>`.

More information about Schlockchain is available in [](about_us).

You can also visit our {ref}`investors`.

## toctree I key value pairs using rst syntax

```{toctree}
:maxdepth: 2
:caption: "Contents:"
   
about_us
```

## toctree II key value pairs using yaml

```{toctree}
---
maxdepth: 1
caption: |
    Contents:
glob:
---

*
```
