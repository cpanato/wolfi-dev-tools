# python

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/chainguard-images/python/actions/workflows/release.yaml/badge.svg)](https://github.com/chainguard-images/python/actions/workflows/release.yaml)

This is a minimal Python image based on Alpine, using Python apks available on the Alpine Community repositories (not built from source as of now).<br/><br/>While this image is being developed, we will stick to the latest stable Python version which at this moment is `3.10.7`. Supported versions in the long term are TBD.

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/python:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `latest` | `sha256:477c7bbee3728ecfc0ceffc34d16a80b4abea5552001981040ca323c9913f6fb`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:477c7bbee3728ecfc0ceffc34d16a80b4abea5552001981040ca323c9913f6fb) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


## Usage

To try out the image, run:

```shell
docker run --rm cgr.dev/chainguard/python python -VV
```

Python version installed 
```
Python 3.10.7 (main, Sep 11 2022, 22:42:41) [GCC 12.1.1 20220630]
```

Pip Version installed 

```shell 
docker run --rm cgr.dev/chainguard/python pip -V
```

```shell
pip 22.2.2 from /usr/lib/python3.10/site-packages/pip (python 3.10)
```


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/python:latest | jq
```

Output:
```
Verification for cgr.dev/chainguard/python:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/python"
      },
      "image": {
        "docker-manifest-digest": "sha256:477c7bbee3728ecfc0ceffc34d16a80b4abea5552001981040ca323c9913f6fb"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8368956347d2538e27b975ac84363f4024924bb4",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/python",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIEOGc+XrzuoDgyKrnDhr5xPeTHwT/dHZRYrg6HPk3lxcAiEAgh5IaPBkhf3+SrAgGnz6/ja15xZNhp7hgE8948lsjAA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzMmY1ZWVhYTZjNDAzMWNhNzNhMjQ0ZGJhOTk4NDZiOTNmZWFmMjAwYTEwYzYwMDIzOTFjN2M1ZTkzNWRlYWM2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURVakhDU3hZdkZpY2pGNjNPR3pFbzRIM3FPNzI0VFc0UHh4dHgwWjVBMDR3SWdHaGk1L3VzQ3FUZXJmQjZDVExEZmtCUUw2VnlEMTkxTGNqenZOMHd4cXZ3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhha05EUVhwSFowRjNTVUpCWjBsVllqZE9WRFp5ZDNwRlJGSldja3hqYUZOUGRYbzRSblZQTVVkVmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hwTlJFbDVUVlJWTkZkb1kwNU5ha2w0VFVSSmVrMUVTWHBOVkZVMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ1VURsWFNYSnhkM0kyVERGWE4wSndOalZRT0hNeVMybHVVV1UzVm00M016SnZOaThLVm04MVJXcFFPREJRWkhkSlpYbHdVR0ZFWjFOb09EUTFSSFZHV25KQ1VHb3ZWVXBzWkRaT1IwaE1VaXRNUm1aTmIyRlBRMEZzUVhkblowcE5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV4VmxSbUNrTnFWREUwYldWbE5HNHphVVpQYzBoTmExazRUVzlKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGQldVUldVakJTUVZGSUwwSkdOSGRZU1ZwaFlVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d6UWpWa1IyaDJZbWs0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFhiSFZOUkd0SFEybHpSMEZSVVVKbk56aDNRVkZGUlVzeWFEQmtTRUo2VDJrNGRtUkhPWEphVnpSMVdWZE9NR0ZYT1hVS1kzazFibUZZVW05a1Ywb3hZekpXZVZreU9YVmtSMVoxWkVNMWFtSXlNSGRHWjFsTFMzZFpRa0pCUjBSMmVrRkNRV2RSU1dNeVRtOWFWMUl4WWtkVmR3cE9aMWxMUzNkWlFrSkJSMFIyZWtGQ1FYZFJiMDlFVFRKUFJHc3hUbXBOTUU0eVVYbE9WRTAwV2xSSk0xbHFhek5PVjBacVQwUlJlazVxVG0xT1JFRjVDazVFYTNsT1IwcHBUa1JCWTBKbmIzSkNaMFZGUVZsUEwwMUJSVVZDUVRWRVkyMVdhR1JIVldkVmJWWnpXbGRHZWxwVVFXMUNaMjl5UW1kRlJVRlpUeThLVFVGRlJrSkNhR3BoUjBad1ltMWtNVmxZU210TVYyeDBXVmRrYkdONU9YZGxXRkp2WWpJMGQwaFJXVXRMZDFsQ1FrRkhSSFo2UVVKQ1oxRlFZMjFXYlFwamVUbHZXbGRHYTJONU9YUlpWMngxVFVsSFMwSm5iM0pDWjBWRlFXUmFOVUZuVVVOQ1NIZEZaV2RDTkVGSVdVRkRSME5UT0VOb1V5OHlhRVl3WkVaeUNrbzBVMk5TVjJOWmNrSlpPWGQ2YWxOaVpXRTRTV2RaTW1JelNVRkJRVWRGUVhGWFlXNTNRVUZDUVUxQlVucENSa0ZwUWxKMFVrRnlOMm92V1d4dGRFTUtXVThyVVVneVp6Wk1hMnN6YUdaMGNEUXdaVzE0UjAwelVHSjJTVEpuU1doQlMxUk1SazlTU0VweE9WQTBaa0pPYmpCMWIzSlhWVFZ1ZUc1emFVbzRZd29yVGxSc1NtOVJiMWt3Um5KTlFXOUhRME54UjFOTk5EbENRVTFFUVRKalFVMUhVVU5OUXpKbWRTdEZhM3B4U1dkeFVGbGxhMWxYWjI1RVRscG9VMGszQ2t4TWVHdEZNMVkyZFZJNWRVMHJZalZOV0dwb05HVXZkSFY2WlhwV05HOXFUMjh5ZVc1blNYZGtNSGxOVlhrd1JYRXdiMUZHWmtwRVUzSXhZMDFQT1hZS1NuaEtXbkJSVlZkWmJ6VlNZM0JIU2tWNlIwZzROMnhJWjA0NVJsWTJXRFJhYVU1NFdXdE5Sd290TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1666491748,
          "logIndex": 5673573,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/python/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/python",
      "githubWorkflowSha": "8368956347d2538e27b975ac84363f4024924bb4",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3305501442",
      "sha": "8368956347d2538e27b975ac84363f4024924bb4"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

