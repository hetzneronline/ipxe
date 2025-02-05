# iPXE for Hetzner

This repository contains all patches that Hetzner has applied to its iPXE build.
It also has a submodule reference to the used git tag of iPXE.

**NOTE:** This repository is a mirror of the internal repository that Hetzner uses to build its iPXE ROM. It is provided as-is and without any kind of support.

## File contents

- `patch/`: Contains all patches that are applied to the iPXE source code.
- `ipxe/`: Contains the iPXE source code (git submodule).
- `embeds/`: Contains all embeds that are used in the iPXE build (only one at this time).
- `ca.crt`: Custom CA certificate that is used for our own cross-signed root CA server. Please see [the Ansible repository for more information](https://github.com/hetznercloud/ansible-role-ipxe-ca).

## Contributing

Unfortunately, we do not accept any kind of contributions to this repository. If you have any questions or feedback, please contact us via a ticket
at [https://robot.hetzner.com/support](https://robot.hetzner.com/support).
