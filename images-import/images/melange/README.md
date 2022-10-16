# melange

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/chainguard-images/melange/actions/workflows/release.yaml/badge.svg)](https://github.com/chainguard-images/melange/actions/workflows/release.yaml)

Container image for running [melange](https://github.com/chainguard-dev/melange) workflows to build APK packages.

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/melange:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `latest` `v0.1.0` | `sha256:ffce3d54824a8c760c9d778ec0e11704930160d6a87407d208545d44c6844c8c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ffce3d54824a8c760c9d778ec0e11704930160d6a87407d208545d44c6844c8c) | `amd64` `arm64` `armv7` |


## Usage

To build the melange workflow in [examples](examples/gnu-hello.yaml):

```
docker run --privileged -v "$PWD":/work cgr.dev/chainguard/melange build /work/examples/gnu-hello.yaml
```

Output will be in the `packages` directory.

To build the melange package for the host architecture:

```
docker run --privileged -v "$PWD":/work cgr.dev/chainguard/melange build --empty-workspace --arch $(uname -m) /work/melange.yaml
```

To get a shell, you can change the entrypoint:

```
docker run --privileged -v "$PWD":/work -it --entrypoint /bin/sh cgr.dev/chainguard/melange

/ # melange version
...
```
Note that melange uses bubblewrap internally, which requires various Linux capabilities, hence the
use of `--privileged`. Because of this requirement, we recommend this image is used only for local
development and testing.


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/melange:latest | jq
```

Output:
```
Verification for cgr.dev/chainguard/melange:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/melange"
      },
      "image": {
        "docker-manifest-digest": "sha256:ffce3d54824a8c760c9d778ec0e11704930160d6a87407d208545d44c6844c8c"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4b427ac92699dcefb48cce90afb2bcf2ebb4253f",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/melange",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIFwcjXx9ER2ThfJsi4M1gWXPlKJjP172IRijce9WA6ybAiAKc5Dm4sTHR+/bBeI1hCxzUSU4dta4idKPy2jCURoGYQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIyZWE1MTRkNzE5MGFhYTdmNDFkM2NmZDJiNTc1YTUzNWYxYTk4ZmU1OGU3YjJmYTYyNDEwOWMzNDY4NTRiYjBhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUM2QjhmNTVnVU5jSmJTMTFJcEoxbFhQdVhWdzZMc1FiL2xmZkFscFVxcFhRSWdFQ1VibVZYOTZTRURUUTZhMmpJOHBPQThiMWdHSDkycG94MFk0Wm41TVZBPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlSRU5EUVhwTFowRjNTVUpCWjBsVlVWbHRla0pvZUhSNkt6aHVZamRRTWxkSk5IZHVhblZQS3pocmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRKTlJFVjNUWHBGTTFkb1kwNU5ha2w0VFVSRk1rMUVSWGhOZWtVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzWkd4dFpVeEViMHh4U3l0c2NIZEVXa2MzWkRKMmVYQjFTMHBUWTJveFdWUlNWbklLVUU5cmRVSlFVbVp2VjJjeEt6SnNNRU5IUVhOWGFVbElZWGxEVW1wdFVqbDNRVkJFTjA4NU1sRXdlVVkzVDJwVlpEWlBRMEZzUlhkblowcE9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV2TUV3NUNrdGhTeTk0V1ZGMVVWaHdaRTE0ZW5sR1ZYUmhSMEYzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGUldVUldVakJTUVZGSUwwSkdPSGRZV1ZwaVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TVd4aVIwWjFXakpWZGt4dFpIQmtSMmd4V1drNU0ySXpTbkphYlhoMlpETk5kbU50Vm5OYVYwWjZXbE0xTlZsWE1YTlJTRXBzQ2xwdVRYWmhSMVpvV2toTmRtSlhSbkJpYWtFMVFtZHZja0puUlVWQldVOHZUVUZGUWtKRGRHOWtTRkozWTNwdmRrd3pVblpoTWxaMVRHMUdhbVJIYkhZS1ltNU5kVm95YkRCaFNGWnBaRmhPYkdOdFRuWmlibEpzWW01UmRWa3lPWFJOUWxsSFEybHpSMEZSVVVKbk56aDNRVkZKUlVOSVRtcGhSMVpyWkZkNGJBcE5SRmxIUTJselIwRlJVVUpuTnpoM1FWRk5SVXRFVW1sT1JFa3pXVmROTlUxcVdUVlBWMUpxV2xkYWFVNUVhR3BaTWxVMVRVZEdiVmxxU21sWk1sbDVDbHBYU21sT1JFa3hUVEpaZDBoQldVdExkMWxDUWtGSFJIWjZRVUpDUVZGUFVUTktiRmxZVW14SlJrcHNZa2RXYUdNeVZYZEtkMWxMUzNkWlFrSkJSMFFLZG5wQlFrSlJVVnBaTW1ob1lWYzFibVJYUm5sYVF6RndZbGRHYmxwWVRYWmlWMVp6V1ZjMWJscFVRV1JDWjI5eVFtZEZSVUZaVHk5TlFVVkhRa0U1ZVFwYVYxcDZUREpvYkZsWFVucE1NakZvWVZjMGQyZFphMGREYVhOSFFWRlJRakZ1YTBOQ1FVbEZaWGRTTlVGSVkwRmtVVUZKV1VwTWQwdEdUQzloUlZoU0NqQlhjMjVvU25oR1duaHBjMFpxTTBSUFRrcDBOWEozYVVKcVduWmpaMEZCUVZsUVpWVlJOMlJCUVVGRlFYZENSMDFGVVVOSlIwSkJMMFpMUjJSWFdsRUtaRVpLZUhoV00yRlJSWEJKYjJVMGIxaG5OVXRZVWxrelpFdFFNVnB3TmtkQmFVRmpha2RaYURkM2VWcFdaMjlKZFZFMFJWRk1TSE53TTBOWFRUQXJSQXBRUXpGeGJXaEljVXBWVDJaWmVrRkxRbWRuY1docmFrOVFVVkZFUVhkT2IwRkVRbXhCYWtWQkswRk9Na2hUUkdaclNGVkNTRkZSZDNWNlZpODFORFEyQ21KWVYzaENWVVJZWVcxRGNIRnVZa2cwTW1zck1YTlhjVzFaZDNSYVZUSkVTa1V4TjNwcUt6aEJha0phTDNSUWMzWTFjMDQwTkVSWVlWbFlNMjl2ZEhjS05GRm1TRTExYm1NdlVHRnZkRkU1TlVad2FUWkJZbFZDYjNVNGJXSmlWVmx6U25kbVNETXhVRGR6YXowS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
          "integratedTime": 1665882205,
          "logIndex": 5187106,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/melange/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/melange",
      "githubWorkflowSha": "4b427ac92699dcefb48cce90afb2bcf2ebb4253f",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3257732682",
      "sha": "4b427ac92699dcefb48cce90afb2bcf2ebb4253f"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [melange](https://github.com/chainguard-dev/melange) and [apko](https://github.com/chainguard-dev/apko).

