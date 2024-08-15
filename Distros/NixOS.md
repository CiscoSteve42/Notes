NixOS Notes 
===========
❄️ Documenting my casual use of NixOS 🐧

Adding Packages on NixOS:
------------------------
❄️ To install a package on your system for regular use, you have to add it to the config file:

* Open the config file `sudo vim /etc/nixos/configuration.nix`

* Scroll down to `environment.systemPackages` and add the package of your choice

* Run `sudo nix-os rebuild switch` afterwards

* Run updates with `sudo nix-channel --update`


Adding RetroArch Emulators:
---------------------------
❄️ You're still gonna add retroarch to the sysPackages, but to get the emulators you'll have to override it as so:

```bash
environment.systemPackages = with pkgs; [
  vim 
  ...
  neofetch
  git
  (retroarch.override {  
    cores = with libretro; [  
      bsnes-hd
      dolphin
      gambatte
      mesen
    ];  
  })
];
```

* If you want to look up emulators, you can search libretro on the site `https://search.nixos.org/packages` or you can use the command `nix search nixpkg libretro` to conduct the search in the terminal.  


Installing Steam
----------------
❄️ Steam is NOT added in the sysPackages area, and requires a few lines to open the firewall and make it work

```bash
...
nixpkgs.config.allowUnfree = true;

programs.steam = {
  enable = true
  remotePlay.openFirewall = true;
  dedicatedServer.openFirewall = true;
  localNetworkGameTransfers.openFirewall = true;
};

# I have mine right here above my other packages and just below RMS repellant option
environment.systemPackages = pkgs; [
  vim
  ...
```


