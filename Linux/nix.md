Adding Packages on NixOS:
------------------------
sudo vim /etc/nixos/configuration.nix

#scroll down to environment.systemPackages

sudo nix-os rebuild switch

Adding RetroArch Emulators on NixOS:
-----------------------------------
(retroarch.override {  
  cores = with libretro; [  
    bsnes  
  ];  
})  

