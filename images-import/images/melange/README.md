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
| `latest` `v0.1.0` | `sha256:5c1b52029e75362010dce45fcfcdd623346a61cd2aa705d00faf87888d93e7e6`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5c1b52029e75362010dce45fcfcdd623346a61cd2aa705d00faf87888d93e7e6) | `amd64` `arm64` `armv7` |


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
        "docker-manifest-digest": "sha256:5c1b52029e75362010dce45fcfcdd623346a61cd2aa705d00faf87888d93e7e6"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "db6958190bdcaeb4c7645208c1696f7049971563",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/melange",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDLLXQRaSk6SYQ5660ERQzToCnacoCfey/SOVw5Dmi5GgIhAL100KUH6GKT+vBwvMXIsSVE7T5KZM990ow97PTKmn74",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmMGFhMzY5NWNmMzAzNWUwYmNjZDNjYTgxYWI5MjczOTZiOTY4NDQzMDNmOTMzZTRhMjcwMDcyM2EyNzM1ZTU0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQjd6M2k2V2ZURmFMaUkwQUhJaUl5Z3hNZjUvbktwTE9oSi9NVHJGRzJ4V0FpQnUyMG52cUJvclkwU0ZlanpBWENiUVBSQStyOVNyazZXMkozTG5yR2g5Tnc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlWRU5EUVhwUFowRjNTVUpCWjBsVlltcDNiVVl3ZG0wd1VtNDVVVWxwUmpCSVJHaFBlREpWTldkRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlhoTlJFVjNUVVJKZVZkb1kwNU5ha2w0VFVSRmVFMUVSWGhOUkVsNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZyTDB0V2VrZGhkekJPWldoTU0wdENZMnR0ZVZsT1NFNUdRWEpzYlVjdlJsTkpabklLVUcxMVZrNXZNM1pFZWtvdlFrTnFUVUk1TldWNVVtRjVNM0E0T0hOM1F6QTJNVWQ2Y0hCS2NDczRlV2MzVXpSTlN6WlBRMEZzU1hkblowcFBUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZsYlZSUENtRTNPRFZrUkdSSVlsaFphRkoxWmpBdlQwOUNhVXRqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGUldVUldVakJTUVZGSUwwSkdPSGRZV1ZwaVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TVd4aVIwWjFXakpWZGt4dFpIQmtSMmd4V1drNU0ySXpTbkphYlhoMlpETk5kbU50Vm5OYVYwWjZXbE0xTlZsWE1YTlJTRXBzQ2xwdVRYWmhSMVpvV2toTmRtSlhSbkJpYWtFMVFtZHZja0puUlVWQldVOHZUVUZGUWtKRGRHOWtTRkozWTNwdmRrd3pVblpoTWxaMVRHMUdhbVJIYkhZS1ltNU5kVm95YkRCaFNGWnBaRmhPYkdOdFRuWmlibEpzWW01UmRWa3lPWFJOUWxsSFEybHpSMEZSVVVKbk56aDNRVkZKUlVOSVRtcGhSMVpyWkZkNGJBcE5SRmxIUTJselIwRlJVVUpuTnpoM1FWRk5SVXRIVW1sT2Ftc3hUMFJGTlUxSFNtdFpNa1pzV1dwU2FrNTZXVEJPVkVsM1QwZE5lRTVxYXpKYWFtTjNDazVFYXpWT2VrVXhUbXBOZDBoQldVdExkMWxDUWtGSFJIWjZRVUpDUVZGUFVUTktiRmxZVW14SlJrcHNZa2RXYUdNeVZYZEtkMWxMUzNkWlFrSkJSMFFLZG5wQlFrSlJVVnBaTW1ob1lWYzFibVJYUm5sYVF6RndZbGRHYmxwWVRYWmlWMVp6V1ZjMWJscFVRV1JDWjI5eVFtZEZSVUZaVHk5TlFVVkhRa0U1ZVFwYVYxcDZUREpvYkZsWFVucE1NakZvWVZjMGQyZFpiMGREYVhOSFFWRlJRakZ1YTBOQ1FVbEZaa0ZTTmtGSVowRmtaMEZKV1VwTWQwdEdUQzloUlZoU0NqQlhjMjVvU25oR1duaHBjMFpxTTBSUFRrcDBOWEozYVVKcVduWmpaMEZCUVZsUVJXcHdZMnBCUVVGRlFYZENTRTFGVlVOSlJuUnRXRTlRV2xKQk5UWUtiakF6UnpabFZsVkNheTh2UVN0bGQwMVhibTUzWlhGVlJVSmtjMEpzUzB0QmFVVkJPR2RMTW5jMGRYcFdaV3RaV0hOTVFubzVjalJpTkVKVlJVaDFNQXBXYlVOeVQyNVRUVUpVYkZSeldHdDNRMmRaU1V0dldrbDZhakJGUVhkTlJHRkJRWGRhVVVsM1JHUnZhRFpEVjNaclUwdFdaMjR3VFZoTVNYRjFkMVp2Q2pjMllWVjJOM1JxY0V0bmMwSTFjVkp1UlhGVE0yYzFLMDlJUkd4MmJtWkVVVEoyU25BM1FrUkJha1ZCTUhwUVlqZExhWHBRT0d4SU5uVTBWQzl1TTJzS0wxZFFZa1Z1TUhoWlJrMURlbmhZU1ZWQ01uZGhaVWRCT0U4dlpFUk5WRmhoVkRkclZXRkZNazB6YnpjS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
          "integratedTime": 1665450038,
          "logIndex": 4857986,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/melange/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/melange",
      "githubWorkflowSha": "db6958190bdcaeb4c7645208c1696f7049971563",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3223306231",
      "sha": "db6958190bdcaeb4c7645208c1696f7049971563"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [melange](https://github.com/chainguard-dev/melange) and [apko](https://github.com/chainguard-dev/apko).

