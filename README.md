# Silverblue Config Automation

This is a personal repository aiming to provion a Fedora Silverblue system according to my customization needs.

This repo is based on the [JayDoubleu](https://github.com/JayDoubleu) [ansiblue work](https://github.com/JayDoubleu/ansiblue) 
and on the repository [asmodeo](https://github.com/pbertera/asmodeo) from [Pietro Bertera](https://github.com/pbertera). Kudos for all your work!

### Prerequisites
Install ansible on silverblue without rpm-ostree
```
python3 -m ensurepip
python3 -m pip install ansible
```

### Configuration
- Edit the `configs/flatpak.yaml` file to customize the list of Flatpak applications installed in the system.
  **NOTE**: Flatpak names are case sensitive. While flatpak is ok with it, creation of symlinks will fail.
- Edit the `configs/toolbox.yaml` to customize the toolbox container, including the packages installed inside it.
- Edit the `configs/host.yaml` file to customize the host and add layered packages using `rpm-ostree`.
- Edit the `configs/host_gnome_dconf.yaml` file to customize the host Gnome settings and behavior.
- Edit the `configs/host_gnome_extensions.yaml` to customize the host Gnome extensions.

### Run
Run the automation using the command:
```
ansible-playbook main.yaml -K
```

**NOTE**: the `-K` option is necessary to elevate user privileges.

### Targeting
It is possible to run only specific customization using Ansible tags:
- `ansible-playbook main.yaml --tags flatpak` <- Run only flatpak tasks
- `ansible-playbook main.yaml --tags toolbox` <- Run only toolbox tasks ( for all toolboxes )
- `ansible-playbook main.yaml --tags fedora-toolbox-35` <- Run only specific toolbox tasks
- `ansible-playbook main.yaml --tags host -K` <- Run only host tasks

### Todo
- Fix the sockpty issue for toolbox shim
