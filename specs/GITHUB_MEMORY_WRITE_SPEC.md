# GitHub Memory Write Spec

## Scope

This spec applies only to the private `innerloop-memory` repository.

## Preconditions

Before a write:

1. The target repository is verified private.
2. The content satisfies `MEMORY_SPEC.md`.
3. No raw journal scan, full transcript, access token, unnecessary identifier, or third-party sensitive detail is included.
4. The write is idempotent with respect to stable memory ID.

## Write pattern

Prefer small commits that describe the semantic change, for example:

`memory: add candidate pattern about late-evening rumination`

If connector permissions require approval, request approval for the write. If write capability is unavailable, output the exact markdown content and intended path for manual commit.
