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
| `latest` `v0.1.0` | `sha256:278d56fa1070115e6f65d940ea35bbee23aea746779521c3b0f096a91827da60`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:278d56fa1070115e6f65d940ea35bbee23aea746779521c3b0f096a91827da60) | `amd64` `arm64` `armv7` |


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
        "docker-manifest-digest": "sha256:278d56fa1070115e6f65d940ea35bbee23aea746779521c3b0f096a91827da60"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "fb8baee7fdea82e0f9f7f0e0c76b6765904b35ca",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/melange",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQD0ShCOIBr1OoHgn974TfNmTcdXnbSaWuOW3Woax9TcFAIgUJqlXWQe1fTnXdBtWMUNn97HUum+hrkmNmrbg7n3ePc=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5ZDEwMDNkOTMzNmFhNzg1ZTJlMTk5OTU4ZjAzYmM5OTM2OTY1ZDU1OWI2YjQ3YTMxZDRkYTc2ZmIxNDVmZjgzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNCOUFKbG1oS2JwcXlVcmVVemhZaVlkR1loUC9rRXFnVGozTHAwQjQ3cjF3SWhBSzkwWlBLUFRQYXVVTkw2UmE3QlVQeHZ4d3VWQTc0ZGRiVytGcGNvdnRjUyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlWRU5EUVhwUFowRjNTVUpCWjBsVlNTczBRMEZIT0ZKRldsVkpWV2xOTTFCYVREWTNjRXN3Tm1SemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRSTlJFVjNUVlJGTkZkb1kwNU5ha2w0VFVSRk5FMUVSWGhOVkVVMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZIYTFJNE1HeHhNRmN6Y1RCYUszZDRTWFZVU0ZKeFRFNU5RVTl0Yms1RFRGUjBiMVlLY1d0ck1YSnBhWE0wT0ZKbU5XcFhVa3c1UkZSWVpXTnNZWFpqU0U1VlNVcE5WbEYwTnpCSk1qVXJTa3BMVHl0bGQzRlBRMEZzU1hkblowcFBUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOUkdKNUNrSTFTRVpVUlRsNWVXaFdZbUl2YUcxek9TdFZURXBCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGUldVUldVakJTUVZGSUwwSkdPSGRZV1ZwaVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TVd4aVIwWjFXakpWZGt4dFpIQmtSMmd4V1drNU0ySXpTbkphYlhoMlpETk5kbU50Vm5OYVYwWjZXbE0xTlZsWE1YTlJTRXBzQ2xwdVRYWmhSMVpvV2toTmRtSlhSbkJpYWtFMVFtZHZja0puUlVWQldVOHZUVUZGUWtKRGRHOWtTRkozWTNwdmRrd3pVblpoTWxaMVRHMUdhbVJIYkhZS1ltNU5kVm95YkRCaFNGWnBaRmhPYkdOdFRuWmlibEpzWW01UmRWa3lPWFJOUWxsSFEybHpSMEZSVVVKbk56aDNRVkZKUlVOSVRtcGhSMVpyWkZkNGJBcE5SRmxIUTJselIwRlJVVUpuTnpoM1FWRk5SVXRIV21sUFIwcG9XbGRWTTFwdFVteFpWR2Q1V2xSQ2JVOVhXVE5hYWtKc1RVZE5NMDV0U1RKT2Vsa3hDazlVUVRCWmFrMHhXVEpGZDBoQldVdExkMWxDUWtGSFJIWjZRVUpDUVZGUFVUTktiRmxZVW14SlJrcHNZa2RXYUdNeVZYZEtkMWxMUzNkWlFrSkJSMFFLZG5wQlFrSlJVVnBaTW1ob1lWYzFibVJYUm5sYVF6RndZbGRHYmxwWVRYWmlWMVp6V1ZjMWJscFVRV1JDWjI5eVFtZEZSVUZaVHk5TlFVVkhRa0U1ZVFwYVYxcDZUREpvYkZsWFVucE1NakZvWVZjMGQyZFpiMGREYVhOSFFWRlJRakZ1YTBOQ1FVbEZaa0ZTTmtGSVowRmtaMEZKV1VwTWQwdEdUQzloUlZoU0NqQlhjMjVvU25oR1duaHBjMFpxTTBSUFRrcDBOWEozYVVKcVduWmpaMEZCUVZsUWIyMHZWRlZCUVVGRlFYZENTRTFGVlVOSlVVUm5ObEZ3ZEVsNmQxTUtXRVJGYmpsdk1HMW1PVU01THpKM1NtbHFiR0pIVkhCM1ZqRmFNVU5yZWk4cmQwbG5aVEo2UVRJNE1HUndSMFJsZWxOWE9FTnlhVU5pVDBKRmQyWnlNUXBUU1ZJelVXWlZjVXRDUjNrME1UUjNRMmRaU1V0dldrbDZhakJGUVhkTlJHRkJRWGRhVVVsNFFVa3dkRTQzYVN0Nk1YaFFjelZHTkdkeVRVTXpSbHB0Q2pacFVVcFNhMmx0Y0dKVGVHdE5jR0ZOVld4NWJFeHRNblJNVDAweFNYWnVaazVEUWxoSWRqZHBaMGwzUjBOT05XTk1ZbVpZVTJaS1RHRldiVVppTUdJS1pGZHVhSFJhYkVSMFJEWjROa2g0VGxaaGNrdFdWMGMzWm5OWlIwOW1VM1pvTlV4U05WRklkekZ6VGtvS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
          "integratedTime": 1666054886,
          "logIndex": 5316540,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/melange/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/melange",
      "githubWorkflowSha": "fb8baee7fdea82e0f9f7f0e0c76b6765904b35ca",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3269753239",
      "sha": "fb8baee7fdea82e0f9f7f0e0c76b6765904b35ca"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [melange](https://github.com/chainguard-dev/melange) and [apko](https://github.com/chainguard-dev/apko).

