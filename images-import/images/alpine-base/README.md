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
| `latest` | `sha256:d44665b0166b0e5232e5259f4373cf0f3d3c8fec86682a8648458e15542cc24c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:d44665b0166b0e5232e5259f4373cf0f3d3c8fec86682a8648458e15542cc24c) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:d44665b0166b0e5232e5259f4373cf0f3d3c8fec86682a8648458e15542cc24c"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5bb45ba2ba16fd0298e0516b670f968dc90da590",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/alpine-base",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQClYBg+zryO9U4Jri8MEV6QNkRAhJp1ycdOIstq/XYmlwIhAJkZxTW51AVZtStUuYRyBDVIU1kH03/T5RtE95KEFVaI",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlOThlYmYzYjU4NjNmM2NlYjIwYWZiNDMyNzE3ZmI5MWM2ZTA2OWZmMTAxNjg0ZWFlYTIyNjdkYzZmZmYwZDY1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNJLzNnd3YrM0JBK3Y4WUU3d1d2TU9WM2s2OGRFQnIxN1d6QVZBTStRZk5nSWhBUDJVcWR6eWJiaWVHYk1DQUFiaXc5S0lwbDJyOGRYQ0Q2bTdzQmErZW40OSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjBWRU5EUVhweFowRjNTVUpCWjBsVlZuZEVTVUk0YjBKTGJtNXhMMVZXYlUwemVYSXhXVmhKWVVwdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1RCTlJFVjVUbnBSZDFkb1kwNU5ha2w0VFVSSk1FMUVSWHBPZWxGM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZET0d4dlIzUTFSall5TlRkUmFrcEJVV2x2UTJveFRqRjFjbEZHVG1OSU1YQm1SRElLTjA5UEswaHNlVkJNZDBkb1NXNHpTbFpCV2twc00zSkdSM2xXVTI5cFV6UkVWMWRTT1VSeFEyWXhhR3BuTmtWT2NFdFBRMEZzYTNkblowcFdUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZVTXpkV0NraG9RMnBVZDB3M1RFVTVaVWxxYVZwc1kxVmtkR2RuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJKUldVUldVakJTUVZGSUwwSkhUWGRaV1ZwbVlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5Um5OalIyeDFXbE14YVZsWVRteE1lVFZ1WVZoU2IyUlhTWFprTWpsNVlUSmFjMkl6WkhwTU0wcHNZa2RXYUdNeVZYVmxWMFowQ21KRlFubGFWMXA2VERKb2JGbFhVbnBNTWpGb1lWYzBkMDlSV1V0TGQxbENRa0ZIUkhaNlFVSkJVVkZ5WVVoU01HTklUVFpNZVRrd1lqSjBiR0pwTldnS1dUTlNjR0l5TlhwTWJXUndaRWRvTVZsdVZucGFXRXBxWWpJMU1GcFhOVEJNYlU1MllsUkJWMEpuYjNKQ1owVkZRVmxQTDAxQlJVTkNRV2g2V1RKb2JBcGFTRlp6V2xSQk1rSm5iM0pDWjBWRlFWbFBMMDFCUlVSQ1EyY3hXVzFKTUU1WFNtaE5iVXBvVFZSYWJWcEVRWGxQVkdoc1RVUlZlRTV0U1RKT2VrSnRDazlVV1RSYVIwMDFUVWRTYUU1VWEzZE5RbmRIUTJselIwRlJVVUpuTnpoM1FWRlJSVVJyVG5sYVYwWXdXbE5DVTFwWGVHeFpXRTVzVFVOelIwTnBjMGNLUVZGUlFtYzNPSGRCVVZWRlNGZE9iMWxYYkhWYU0xWm9ZMjFSZEdGWE1XaGFNbFo2VERKR2MyTkhiSFZhVXpGcFdWaE9iRTFDTUVkRGFYTkhRVkZSUWdwbk56aDNRVkZaUlVRelNteGFiazEyWVVkV2FGcElUWFppVjBad1ltcERRbWxSV1V0TGQxbENRa0ZJVjJWUlNVVkJaMUkzUWtoclFXUjNRakZCUVdobkNtdDJRVzlWZGpsdlVtUklVbUY1WlVWdVJWWnVSMHQzVjFCalRUUXdiVE50ZGtOSlIwNXRPWGxCUVVGQ2FFRmxZVkZTU1VGQlFWRkVRVVZaZDFKQlNXY0tWRmRYZEU1YU0ya3JWR1J3Ym1NNE15OHZjSGhTWkRGdGJFeElNbmRXZW1ObFpGWnNhSEVyY1VaMGMwTkpRV1J2YVhkdVlXcFRiMDFZVkRkcGMyc3JUZ294VWxKUmFuWjZTVXR4YW5aVGNuY3lTemRKU1c4M2RWaE5RVzlIUTBOeFIxTk5ORGxDUVUxRVFUSnJRVTFIV1VOTlVVTmllWHAzTVVsRk9FcFNkVEpqQ2tGaldsYzBXbWxJV2poTlRuTklZMDF5VUVwS2IzUmtlbEZ3UlRGR1VHTTRibFl4Tm05b05qbDJWMWhQV0VWelowZFVRVU5OVVVOMEszRjZhVXR5VDBzS1lVSldaVFppZURNMU1rRnplbUZHZFRaME1VVnZPRTFHWWs0M1RVdEdNSHByU1RaVk16UTFVSFZaYm1VeVlUTkZURmQ0ZWxWU01EMEtMUzB0TFMxRlRrUWdRMFZTVkVsR1NVTkJWRVV0TFMwdExRbz0ifX19fQ==",
          "integratedTime": 1666574884,
          "logIndex": 5731310,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/alpine-base/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/alpine-base",
      "githubWorkflowSha": "5bb45ba2ba16fd0298e0516b670f968dc90da590",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3309346016",
      "sha": "5bb45ba2ba16fd0298e0516b670f968dc90da590"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

