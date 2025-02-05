# iPXE for Hetzner

This repository contains all patches that Hetzner has applied to its iPXE build.
It also has a submodule reference to the used git tag of iPXE.

**NOTE:** This repository is a mirror of the internal repository that Hetzner uses to build its iPXE ROM. It is provided as-is and without any kind of support.

## File contents

- `patch/`: Contains all patches that are applied to the iPXE source code.
- `ipxe/`: Contains the iPXE source code (git submodule).
- `embeds/`: Contains all embeds that are used in the iPXE build (only one at this time).
- `ca.crt`: Custom CA certificate that is used for our own cross-signed root CA server. Please see [the Ansible role repository for more information](https://github.com/hetznercloud/ansible-role-ipxe-ca).

## Contributing

Unfortunately, we do not accept any kind of contributions to this repository. If you have any questions or feedback, please contact us via a ticket
at [https://robot.hetzner.com/support](https://robot.hetzner.com/support).

## FAQ

### Why do you use a commit/version from 2023?

iPXE is a rolling-release project that does not have any (usable) tags or releases. Every new feature, bug fix, optimisation, and so on must be re-evaluated and tested across all the hardware platforms we support.

If a critical bug fix is required, we cherry-pick the commit from the iPXE repository and apply it here. This ensures that we provide a stable and tested iPXE binary. If a fix requires more work or there is a justified reason, we may update the base commit to a newer one; however, this is not done regularly.

### Why is there a custom embed?

Some servers may have an empty CMOS battery or an incorrect RTC time, causing the certificate expiry check to fail. To prevent this, we synchronise the time before loading the iPXE script.

### Why do you use a custom CA certificate?

We cross-sign the root CA certificates with our own CA to ensure HTTPS support without requiring a connection to a system outside the Hetzner network.

The cross-signing process follows the same approach as the original iPXE binary. For a more in-depth explanation of how certificate validation works in iPXE, please refer to the [Ansible role repository](https://github.com/hetznercloud/ansible-role-ipxe-ca).
