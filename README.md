# Ignition

Ignition is the utility used by CoreOS Container Linux, Fedora CoreOS, and RHEL CoreOS to manipulate disks during the initramfs. This includes partitioning disks, formatting partitions, writing files (regular files, systemd units, etc.), and configuring users. On first boot, Ignition reads its configuration from a source of truth (remote URL, network metadata service, hypervisor bridge, etc.) and applies the configuration.

## Usage

Odds are good that you don't want to invoke Ignition directly. In fact, it isn't even present in the Container Linux root filesystem. Take a look at the [Getting Started Guide][getting started] for details on providing Ignition with a runtime configuration.

## Contact

- Mailing list: [coreos@lists.fedoraproject.org](https://lists.fedoraproject.org/archives/list/coreos@lists.fedoraproject.org/)
- IRC: #[fedora-coreos](irc://irc.freenode.org:6697/#fedora-coreos) on freenode.org
- Bugs: [issues][issues]

## Contributing

See [CONTRIBUTING](CONTRIBUTING.md) for details on submitting patches and the contribution workflow.

To help triage or fix bugs, see the current [Ignition issues](https://github.com/coreos/ignition/issues/).

## Reporting Bugs

- To report a bug, use the [bug tracker][issues]

## Config Validation

To validate a config for Ignition there are binaries for a cli tool called `ignition-validate` available [on the releases page][releases]. There is also an ignition-validate container: `quay.io/coreos/ignition-validate`.

Example:
```
# This example uses podman, but docker can be used too
podman run --rm -i quay.io/coreos/ignition-validate - < myconfig.ign
```

## Branches

There are two branches:
- `master`: uses Ignition V2 (spec 3) and is used by Fedora CoreOS
  and Red Hat CoreOS starting with version 46.82.
- `spec2x` works with the `spec2x` branch of ignition-dracut
  and is currently used by CL and RHEL CoreOS, which (for
  now) targets Ignition v0.x (spec 2).

## Legacy Ingition-Dracut:

With commit d1f1417dd95425bbc1a5dcdebc777b93ecb77c46 the old [Ingition-Dracut](https://github.com/coreos/ignition-dracut) commit 6b1d128c6ba2d77825d214ada238a4826e420d40 was merged into Ignition itself. In [Fedora Tracker #511](https://github.com/coreos/fedora-coreos-tracker/issues/511) it was proposed and accepted to merge the two repos together.

The CoreOS specific Dracut modules have been moved into [Fedora CoreOS Config](https://github.com/coreos/fedora-coreos-config).

[getting started]: doc/getting-started.md
[issues]:  https://github.com/coreos/ignition/issues/new/choose
[releases]: https://github.com/coreos/ignition/releases
[online-validator]: https://coreos.com/validate/
