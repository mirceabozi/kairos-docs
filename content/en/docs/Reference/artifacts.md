---
title: "Artifact Naming Convention"
linkTitle: "Artifact Naming Convention"
weight: 1
date: 2023-07-19
description: >
  Detailed information about how we name our artifacts including repositories.
---

# Artifacts

Artifacts are named using the following convention:

```
kairos-<support>-<type>-<flavor>-<arch>-<device>-<version>[-<non-image-type>].<extension>
```

Where:

- `<support>`: `official` or `community`
- `<type>`: `core` or `standard`
- `<flavor>`: Underlying Linux distribution e.g. `ubuntu`, `debian`, `fedora`, `alpine`, etc
- `<arch>`: `x86_64`, `arm64`, `armhf`, `aarch64`, etc
- `<device>`: either the specific device name, e.g. `rpi64` or `generic` for generic images
- `<version>`: the version of Kairos e.g. `1.0.0` can also include the K3S version e.g. `1.0.0-k3s1` in case of Kairos Standard
- `<non-image-type>`: only used for artifacts that are not images e.g. `trivy` for Trivy scans

## Examples

- `kairos-official-core-ubuntu-x86_64-generic-1.0.0.iso`
- `kairos-official-standard-ubuntu-arm64-rpi64-1.0.0-k3s1.img`
- `kairos-community-core-alpine-aarch64-generic-1.0.0-trivy.sarif`

# Repositories

<alert type="warning">
  The repositories are not yet available, they will be published soon.
</alert>

```
domain/kairos/<support>-<type>-<flavor>-<device>[-<extension>]:<version>
```

This nomenclature for repositories lacks some information that is included in the artifacts for the following reasons:

1. Docker repositories can be multi-arch, so the same image can be used in different architectures and therefore the name does not include the architecture.
2. The version is not included in the repository name, but in the tag of the image.
3. The name Kairos is already part of the repository name, so it is not included in the image name.

- quay.io/kairos/official-core-ubuntu-generic:v1.0.0

# Framework images

All different framework images are stored in the same repository, so the details of the image are included in the tag and don't require all the information in the name:


```
domain/kairos/framework:<version>_<flavor>
```

## Examples

- quay.io/kairos/frameworks:v1.0.0_ubuntu
- quay.io/kairos/frameworks:master_alpine