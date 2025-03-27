criar xorg file pra forcar x11 usar a nvidia nao o integrado

mkdir -p /etc/X11/xorg.conf.d
nano /etc/X11/xorg.conf.d/10-nvidia.conf

com o conteudo dentro de 10-nvidia.conf sendo

Section "Module"
    Load "modesetting"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1:0:0"  # This might need adjustment based on your system
    Option "AllowEmptyInitialConfiguration"
EndSection

(se por algum motivo voce for alguma outra pessoa querendo usar isso altere o ID do pci para a sua nvidia "lspci | grep -i nvidia" -> use isso pra ver qual slot esta)


configurar o sddm (se voce utiliza outro Display Manager so procurar por ele)
mkdir -p /usr/share/sddm/scripts
nano /usr/share/sddm/scripts/Xsetup

so adiiconar isso no xsetup
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
