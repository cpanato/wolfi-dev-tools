# alpine-base

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/chainguard-images/alpine-base/actions/workflows/release.yaml/badge.svg)](https://github.com/chainguard-images/alpine-base/actions/workflows/release.yaml)

Alpine base image built with [apko](https://github.com/chainguard-dev/apko). Uses packages from the [Alpine distribution](https://www.alpinelinux.org/).

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/alpine-base:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `latest` | `sha256:c6f28672eae18a5b75371ce0eff534df4aecaf14c2a5fd96782589df4d9d17e3`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c6f28672eae18a5b75371ce0eff534df4aecaf14c2a5fd96782589df4d9d17e3) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


## Usage

```
docker run cgr.dev/chainguard/alpine-base echo "hello"
```

See the [examples/](./examples/) directory for how
to use this as a base image.


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/alpine-base:latest | jq
```

Output:
```
Verification for cgr.dev/chainguard/alpine-base:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/alpine-base"
      },
      "image": {
        "docker-manifest-digest": "sha256:c6f28672eae18a5b75371ce0eff534df4aecaf14c2a5fd96782589df4d9d17e3"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5d2e49e872d5f9ebfe1437f3231d5c3c72700f3e",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/alpine-base",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDVY+ci63lBY9Y6pC5D6izoavVGGgrMvdVTi4R1ijoD7QIhAN+qPq6+4s1sU4EQDk7Y5RSRcv7O+wcpPZQyiKbmH4Q5",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwNjNjN2Y0M2YzYjY4OTMwYzAyNTlmODZkZGQ3NzI1YzM0OTA5NTJhY2MzZjM1NzI2NmZlOTk2NjIyZGQwNzU3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ0xtZFhucDNFNzM3a1hjdW9QM3dRSHQwVi9YdTgvUStKOTJWdGI1UEF6NkFpRUFreFlWYUNCRmZjT3MrYi9oRkZOYjFJZWJ4VlNFVU81d0NsREJQSm1EcjBFPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjBSRU5EUVhwMVowRjNTVUpCWjBsVlJsTkZLMU5wYW1ZMkwxWXhOemxTTjA5eE5EVnJRa1J1U0RWRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRCTlJFVjVUbFJGTVZkb1kwNU5ha2w0VFVSRk1FMUVSWHBPVkVVeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZQZG1wQ1NreDJUM1JEVm1vdlRWZHVUM1ZFTW5rMlJrUnRiMHhEVVhacFp5OXNiVkFLUzA1eGEya3lURTlCZUZkelZsTlFVV1JZWWxWblkyMDBNM0JYUmxOT1VtbFZUM0I0TVZGNmJTOXRjak0zYWtRMldqWlBRMEZzYjNkblowcFhUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZaVGs1WENraE5TRVZ6Uld4VGRraG5Za0poTkU1UEx6QTVlRk5uZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJKUldVUldVakJTUVZGSUwwSkhUWGRaV1ZwbVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5Um5OalIyeDFXbE14YVZsWVRteE1lVFZ1WVZoU2IyUlhTWFprTWpsNVlUSmFjMkl6WkhwTU0wcHNZa2RXYUdNeVZYVmxWMFowQ21KRlFubGFWMXA2VERKb2JGbFhVbnBNTWpGb1lWYzBkMDlSV1V0TGQxbENRa0ZIUkhaNlFVSkJVVkZ5WVVoU01HTklUVFpNZVRrd1lqSjBiR0pwTldnS1dUTlNjR0l5TlhwTWJXUndaRWRvTVZsdVZucGFXRXBxWWpJMU1GcFhOVEJNYlU1MllsUkJWMEpuYjNKQ1owVkZRVmxQTDAxQlJVTkNRV2g2V1RKb2JBcGFTRlp6V2xSQk1rSm5iM0pDWjBWRlFWbFBMMDFCUlVSQ1EyY3hXa1JLYkU1RWJHeFBSR041V2tSV2JVOVhWbWxhYlZWNFRrUk5NMXBxVFhsTmVrWnJDazVYVFhwWmVtTjVUbnBCZDFwcVRteE5RbmRIUTJselIwRlJVVUpuTnpoM1FWRlJSVVJyVG5sYVYwWXdXbE5DVTFwWGVHeFpXRTVzVFVOelIwTnBjMGNLUVZGUlFtYzNPSGRCVVZWRlNGZE9iMWxYYkhWYU0xWm9ZMjFSZEdGWE1XaGFNbFo2VERKR2MyTkhiSFZhVXpGcFdWaE9iRTFDTUVkRGFYTkhRVkZSUWdwbk56aDNRVkZaUlVRelNteGFiazEyWVVkV2FGcElUWFppVjBad1ltcERRbWxuV1V0TGQxbENRa0ZJVjJWUlNVVkJaMUk0UWtodlFXVkJRakpCUVdobkNtdDJRVzlWZGpsdlVtUklVbUY1WlVWdVJWWnVSMHQzVjFCalRUUXdiVE50ZGtOSlIwNXRPWGxCUVVGQ1p6bFJXV1JITUVGQlFWRkVRVVZqZDFKUlNXY0tZMDlrU0RZemNVMXJhbmhGT0dWQ1JrUkxSelZWVW5aaWMwRlNVRkJxVVRkRFJrVmhOemh4UmpOSVNVTkpVVVF4T1V4elNURXlSak4zYTNCbFJVSmtkQW92Y1RSaGVtOTZZbEpFVDBnMGNuYzNlakIzUVVOVVVUY3JSRUZMUW1kbmNXaHJhazlRVVZGRVFYZE9ia0ZFUW10QmFrRXhZVWRyV1RkalpVSk9jSGxqQ25vM1pWZDVjakF5YUZGRk0weGFUR1ZhVWt0QlRVcDNORGsxZFU0NU9IRTJkWEJzZFVWcGQzWXliRU5xZFVKNUszTkpPRU5OU0c4eFQxbzJkRlJKZEc4S1ZtNDFjRzEwU0ZrMFduaG5OVzVpY2xwd1IwTm9OVTlEVVdaT01FOVZOVEZNUm05NFMyMDVMM2QzUkRWQ0sxSlpaQ3RoTUV0blBUMEtMUzB0TFMxRlRrUWdRMFZTVkVsR1NVTkJWRVV0TFMwdExRbz0ifX19fQ==",
          "integratedTime": 1665710739,
          "logIndex": 5063056,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/alpine-base/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/alpine-base",
      "githubWorkflowSha": "5d2e49e872d5f9ebfe1437f3231d5c3c72700f3e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3246802984",
      "sha": "5d2e49e872d5f9ebfe1437f3231d5c3c72700f3e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

