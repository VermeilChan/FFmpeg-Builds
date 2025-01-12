# FFmpeg Static Auto-Builds

| **Platform**                  | **Details**                                                                        |
|-------------------------------|------------------------------------------------------------------------------------|
| **Windows (x64)**             | - Supports Windows 7 and newer, with UCRT installed.                               |
|                               | - Minimum guaranteed version: Windows 10 22H2.                                     |
|                               | - No guarantees on versions older than Windows 10 22H2.                            |
| **Linux (x64)**               | - Compatible with RHEL/CentOS 8 (glibc-2.28 + linux-4.18) and newer distributions. |
| **Build Types**               | - FFmpeg master and latest release branches.                                       |

## Auto-Builds

Builds run daily at 5:00 UTC (or GitHubs idea of that time) and are automatically released on success.

### Release Retention Policy

- The last build of each month is kept for two years.
- The last 14 daily builds are kept.
- The special "latest" build floats and provides consistent URLs always pointing to the latest build.

## Package List

For a list of included dependencies check the scripts.d directory.
Every file corresponds to its respective package.

## How to make a build

### Prerequisites

* bash
* docker

### Build Image

* `./makeimage.sh target variant [addin [addin] [addin] ...]`

### Build FFmpeg

* `./build.sh target variant [addin [addin] [addin] ...]`

On success, the resulting zip file will be in the `artifacts` subdir.

### Targets, Variants and Addins

Available targets:
* `win64` (x86_64 Windows)
* `linux64` (x86_64 Linux, glibc>=2.28, linux>=4.18)

Available variants:
* `gpl` Includes all dependencies, even those that require full GPL instead of just LGPL.

All of those can be optionally combined with any combination of addins:
* `2.8`/`4.4`/`5.0`/`5.1`/`6.0`/`6.1`/`7.0` to build from the respective release branch instead of master.
