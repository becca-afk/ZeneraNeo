# OPS-1: Draw the release

## The Release Flow
```mermaid
flowchart TD
    A[Developer runs: npm run release -- patch] --> B{Dirty tree or out of lockstep?}
    B -- Yes --> C[Fails: Refuses to run]
    B -- No --> D[Updates package.json versions & internal ranges]
    D --> E[Refreshes package-lock.json]
    E --> F[Commits: release: vX.Y.Z & tags vX.Y.Z]
    F --> G[Developer pushes tag: git push --follow-tags]
    
    G --> H[GitHub Actions Release Workflow triggers]
    H --> I[Verify tag matches package versions]
    I --> J[Run checks: format, typecheck, vitest]
    J --> K[Run npm pack --dry-run]
    K --> L[Publish packages in dependency order]
    L --> M[Create GitHub Release notes]
    M --> N[Build and push Docker images]
