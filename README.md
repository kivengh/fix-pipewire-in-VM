# fix-pipewire-in-VM
 install & fix pipewire vmware workstation


```bash
pacman -S pipewire wireplumber pipewire-pulse
```

```bash
mkdir -p ~/.config/wireplumber/wireplumber.conf.d/
```

```bash
vim ~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf
```

```
monitor.alsa.rules = [
  {
    matches = [
      { node.name = "~alsa_output.*" },
      { node.name = "~alsa_input.*" }
    ]
    actions = {
      update-props = {
        api.alsa.period-size = 1024
        api.alsa.headroom    = 8192
      }
    }
  }
]
```


```bash
systemctl --user restart wireplumber pipewire pipewire-pulse
```

*need install*  
in arch: pacman -S
in fedora: dnf install
in debian: apt
or your choice 
