Ansible Role: Vulkan
=========

**Note**: This role is in early stages of development and is not suitable for production. Contributions are welcome.

Installs Vulkan drivers and development libraries in Fedora servers.
Currently supports Fedora (+31) and NVIDIA, AMD and Intel platforms.

Requirements
------------

The hardware to be installed on must be Vulkan-compatible. This can be checked using the device's official
documentation or the [Vulkan Hardware Database](https://vulkan.gpuinfo.org/).

Role Variables
--------------

| Variable name       | Default | Description                                                                                                                                   |
|---------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| `gpu_vendor`        | `"all"` | The GPU vendor of the server.  This can be `amd`, `nvidia`, `intel` or `all`.                                                                 |
| `reboot_on_install` | `True`  | Whether to reboot the server after install drivers and libraries.  Keep in mind Vulkan might not work correctly without rebooting the system. |
| `install_devel`     | `True`  | Whether to install development libraries and tools.  Useful for compiling and testing on servers.                                             |

Dependencies
------------

None

Example Playbook
----------------

The following example assumes the host runs on Fedora with an AMD GPU, and installs drivers and development libraries. Reboot after installing is also recommended.

    - hosts: gpuserver
      vars:
        gpu_vendor: "amd"
        install_devel: True
        reboot_on_install: True
      roles:
         - { role: atorresm.vulkan }

License
-------

This role is licensed under the GPL3. Check the LICENSE file for more information.