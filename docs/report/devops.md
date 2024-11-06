---
sidebar_position: 5
---

# DevOps

```mermaid
flowchart LR
    A[build-matrix]-- ✅--> B[format] -- ✅--> G
    B -- ✅ --> D[release] -- ✅ --> G[success]
    A -- ✅ --> D
    A -- ✅--> C[linter] -- ✅ --> D
    D -- ✅ --> E[docs]  -- ✅ --> G
    D -- ✅ --> F[deploy-image]  -- ✅ --> G
    C -- ✅ --> G
    A -- ✅ --> G
```