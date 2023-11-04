# 2. Storage Class Provider

Date: 2022-11-04

## Status

Accepted

## Context

Zarf's init process traditionally requires a storage class to be pre-existing in the cluster and while this is relatively easy to configure on single node clusters or on cloud connected clusters, multi-node on-prem clusters like RKE2 require more work and create a chicken and egg scenario within the airgap.

To solve this we need to choose a storage class provider and implement an init package that can bootstrap it within a cluster on `zarf init`:

1. **Longhorn**

PROS:

- Longhorn is developed by Rancher and integrates well into RKE2 (where this problem has presented itself most)
- The Zarf team, and other Defense Unicorns members are already familiar with Longhorn and it's install process

CONS:

- Longhorn lacks other features that might be useful (like direct S3 support)

2. **Rook / Ceph**

PROS:

- Rook / Ceph has more advanced features (like direct S3 support)

CONS:

- The Zarf team, and other Defense Unicorns members have less familiarity with Rook / Ceph and it's install process

3. **NFS**

PROS:

- NFS has been around for a while and has a lot of support across many projects

CONS:

- NFS requires something else to exist in the environment first and may not be a great choice for entirely bare airgap environments.

## Decision

For now we have decided to go with Longhorn due to the familiarity and in order to get something working quickly.  Once we prove out the process for getting a storage class up on init we can explore Rook Ceph as well later (since it also has charts and _should_ work in a similar way).

## Consequences

This will mean we only have a standard storage class without additional features like direct S3 support but we should be able to explore that later, and that wasn't the direct goal of this repo.
