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
| `latest` `v0.1.0` | `sha256:76d88908cca574b1b75c372fa35f9e467a615f92f1a0fb4614d7333c969c04e5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:76d88908cca574b1b75c372fa35f9e467a615f92f1a0fb4614d7333c969c04e5) | `amd64` `arm64` `armv7` |


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
        "docker-manifest-digest": "sha256:76d88908cca574b1b75c372fa35f9e467a615f92f1a0fb4614d7333c969c04e5"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8a15b44633b04ca312fda2b196697bcaf06079d0",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/melange",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDneejCpFLPwJoPG4LD6VXXtiO8YX96HjohPMuQRmoXeAIhANKfNRpCSuYuTqq6wElnoOAD0Y64G7ZVp1okdEX989sB",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiZDQwMTMxMGE1MWUwMzRmODM4NTgyZjBlYzA0YTlhNDdmODVmYTkzZWUxMjMxODZkMTdkZTdiMDdmZjI0N2NmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUMxYlRPZ3JSOS9pRmVPaWdJbno4SDVZUDBDOEdvaFNuQVpDOXJhZFhVS0dnSWhBSXVMYzVaRGJ0WGJTVnowbGxxNjBrVGRHSEFZMW1hWTROMzAyTGtBRWE5NyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlWRU5EUVhwUFowRjNTVUpCWjBsVldGUmlhVXd2UkdrdkwwUmFlSEJhVFRoa2MwZ3lUbmhsY0c5RmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRWTlJFVjNUWHBWTTFkb1kwNU5ha2w0VFVSRk5VMUVSWGhOZWxVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYzVldGNGFWUTVValJWVW1sM1VVWklka0YzVGtoTE9TOVZUVEZ1VmxaWFVpOTJMMWdLSzFscFRsVnBUaXRaV21wb2VXRkpZVTVSTTBwTFFuaElWWEJsUVRsUFNrZzFVVEJUUjFSblNEaHhkVU42YTI4NVYyRlBRMEZzU1hkblowcFBUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV2U3pKRUNuWnZiMFJGTmtoYU5FNVlUR3BCVFhkVVVsbGFUa2MwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGUldVUldVakJTUVZGSUwwSkdPSGRZV1ZwaVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TVd4aVIwWjFXakpWZGt4dFpIQmtSMmd4V1drNU0ySXpTbkphYlhoMlpETk5kbU50Vm5OYVYwWjZXbE0xTlZsWE1YTlJTRXBzQ2xwdVRYWmhSMVpvV2toTmRtSlhSbkJpYWtFMVFtZHZja0puUlVWQldVOHZUVUZGUWtKRGRHOWtTRkozWTNwdmRrd3pVblpoTWxaMVRHMUdhbVJIYkhZS1ltNU5kVm95YkRCaFNGWnBaRmhPYkdOdFRuWmlibEpzWW01UmRWa3lPWFJOUWxsSFEybHpSMEZSVVVKbk56aDNRVkZKUlVOSVRtcGhSMVpyWkZkNGJBcE5SRmxIUTJselIwRlJVVUpuTnpoM1FWRk5SVXRFYUdoTlZGWnBUa1JSTWsxNlRtbE5SRkpxV1ZSTmVFMXRXbXRaVkVwcFRWUnJNazVxYXpOWmJVNW9DbHBxUVRKTlJHTTFXa1JCZDBoQldVdExkMWxDUWtGSFJIWjZRVUpDUVZGUFVUTktiRmxZVW14SlJrcHNZa2RXYUdNeVZYZEtkMWxMUzNkWlFrSkJSMFFLZG5wQlFrSlJVVnBaTW1ob1lWYzFibVJYUm5sYVF6RndZbGRHYmxwWVRYWmlWMVp6V1ZjMWJscFVRV1JDWjI5eVFtZEZSVUZaVHk5TlFVVkhRa0U1ZVFwYVYxcDZUREpvYkZsWFVucE1NakZvWVZjMGQyZFpiMGREYVhOSFFWRlJRakZ1YTBOQ1FVbEZaa0ZTTmtGSVowRmtaMEZKV1VwTWQwdEdUQzloUlZoU0NqQlhjMjVvU25oR1duaHBjMFpxTTBSUFRrcDBOWEozYVVKcVduWmpaMEZCUVZsUWRIaE5RWGhCUVVGRlFYZENTRTFGVlVOSlVVTnJjVUpoU1VKclJrUUtWblJKUVhNMlVEQTNORFpJUVRoQmVUSnFMMjB4YzJkclp6QlZZMVZxUTNKSFFVbG5UMnROYlRWeVVHTjRaVmhPUVhkUVZIbHJVREpFZEZKWk1UUkxkZ3BGVmtzMWMzVnlhMHBLVURObU5sVjNRMmRaU1V0dldrbDZhakJGUVhkTlJHRkJRWGRhVVVsNFFVOWxhR3RuVTJJNGJDOUllazVFWmpOWEx6TjNjQzlUQ205UVVWbzFWak5IV25ncmVtSkNWV280VkZGbk9GZEZlRXBYUkZVMVRGZG9iMko1UnpVdmVreGtVVWwzVkdORllXdGthMmc0VGpSamQwRldla2hDZURJS2RXZGtObmcwYjNsNWRrWnZlbEJSVGpWVlUxUkJSMEoxVDNKTVYwbEtSRkV6WVVWcVVuaHFNVVJDUkdFS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
          "integratedTime": 1666141448,
          "logIndex": 5398383,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/melange/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/melange",
      "githubWorkflowSha": "8a15b44633b04ca312fda2b196697bcaf06079d0",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3277986923",
      "sha": "8a15b44633b04ca312fda2b196697bcaf06079d0"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [melange](https://github.com/chainguard-dev/melange) and [apko](https://github.com/chainguard-dev/apko).

