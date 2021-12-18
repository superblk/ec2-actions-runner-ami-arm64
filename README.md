# AMI for self-hosted GitHub actions runner (Linux arm64)

Based on the latest official Ubuntu 18.04 arm64 HVM EBS AMI.

## Build

We use Hashicorp's [packer](https://www.packer.io/) and GitHub actions to build the AMI, see [workflow](.github/workflows/build-ami.yml).

## Usage

Currently no public AMI is published. You can fork this repo and build your own.

Runner binaries are pre-installed in `/home/ubuntu/actions-runner`.

Passwordless sudo is configured for the `ubuntu` user.

## Security

- Do not run self-hosted runners in public repositories (see relevant [GitHub docs](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#self-hosted-runner-security-with-public-repositories))
- This image is designed to run the actions-runner with a non-root user (e.g. `ubuntu`)
- Ephemeral runners (torn down at the end of each workflow run) is probably the safe bet
- Some security hardening of this AMI is probably warranted (contributions are welcome!)

## References

- <https://github.com/actions/runner/blob/main/docs/start/envlinux.md>
- <https://github.com/actions/runner/blob/main/scripts/create-latest-svc.sh>
