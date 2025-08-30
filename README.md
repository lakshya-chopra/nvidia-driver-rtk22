# nvidia-driver-rtk22


Download the NVIDIA .run Driver
```shell
wget https://us.download.nvidia.com/XFree86/Linux-x86_64/550.127.05/NVIDIA-Linux-x86_64-550.127.05.run
```

Blacklist Nouveau

[ref 1](https://askubuntu.com/questions/1463568/why-remover-the-nouveau-drivers)

[ref 2](https://docs.nvidia.com/ai-enterprise/deployment/vmware/latest/nouveau.html)

```shell
echo -e "blacklist nouveau\noptions nouveau modeset=0" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
```

```shell
sudo update-initramfs -u
```

```shell
sudo reboot
```
Install the NVIDIA Driver

```shell
sudo IGNORE_PREEMPT_RT_PRESENCE=1 bash NVIDIA-Linux-x86_64-550.127.05.run
```
This bypasses the check for real-time kernels.

```shell
sudo reboot
```

Now verify:
```shell
nvidia-smi
```

