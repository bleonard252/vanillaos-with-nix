# VanillaOS image with Nix
This is a simple custom [VanillaOS](https://vanillaos.org/) image that includes [Nix](https://nixos.org/download/#download-nix-accordion), the package manager.
- This is kept up-to-date regularly with the base image, `vanilla-os/desktop` (the GNOME image), thanks to a regularly-scheduled GitHub action.

Please check if the builds have succeeded yet before attempting to use this image. If you're ever in doubt, don't. It's not ready yet.

## How to use

- Edit the `/etc/abroot/abroot.json` file with the command: `host-shell pkexec nano /etc/abroot/abroot.json`.
- Change the "name" entry from something like `vanilla-os/desktop` to `bleonard252/vanillaos-with-nix`.  [**Note**: All characters must be in lowercase.]
- Now, Run `abroot upgrade` to switch to your custom image.

## Include Nix in your custom image
If you're building another Vib/VanillaOS custom image, you may add Nix to it by adding the following to the "custom actions" section of your module:

```yaml
  - name: install-nix
    type: includes
    includes:
      - gh:bleonard252/vanillaos-with-nix:main:modules/50-install-nix.yml
```

You could do it yourself with the "shell" module, but doing it this way will keep up with any changes I make to make Nix work.

This recipe and the resultant Vib image are licensed under GNU GPL v3.