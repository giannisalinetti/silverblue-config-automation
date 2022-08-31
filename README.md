# Silverblue Config Automation

This is a personal repository aiming to provion a Fedora Silverblue system according to my customization needs.

This repo is based on the [JayDoubleu](https://github.com/JayDoubleu) [ansiblue work](https://github.com/JayDoubleu/ansiblue) 
and on the repository [asmodeo](https://github.com/pbertera/asmodeo) from [Pietro Bertera](https://github.com/pbertera). Kudos for all your work!

### Prerequisites
Install ansible on silverblue without rpm-ostree
```
python3 -m ensurepip
python3 -m pip install ansible
ansible --version
```

### Run
- Edit `configs/flatpak.yaml`, `configs/toolbox.yaml` and `config/host.yaml` to customize the configurations.
- Run with `ansible-playbook main.yaml -K`
- Flatpak names are case sensitive. While flatpak is ok with it, creation of symlinks will fail.

### Targeting:
- `ansible-playbook main.yaml --tags flatpak` <- Run only flatpak tasks
- `ansible-playbook main.yaml --tags toolbox` <- Run only toolbox tasks ( for all toolboxes )
- `ansible-playbook main.yaml --tags fedora-toolbox-35` <- Run only specific toolbox tasks
- `ansible-playbook main.yaml --tags host -K` <- Run only host tasks

### Todo
- Fix the sockpty issue for toolbox shim
