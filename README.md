# ZjebOS

ZjebOS is a customized Arch Linux desktop live ISO. It uses CachyOS repositories, kernels and system packages as its technical base, while the distribution identity and boot experience are branded as ZjebOS.

## Default applications

The desktop image includes Firefox, Discord, Steam, Spotify Launcher, VLC, OBS Studio, LibreOffice, GIMP, Audacity, Telegram, qBittorrent, pavucontrol and fastfetch. Firefox is already part of the base package set; the remaining applications are declared in `archiso/packages_desktop.x86_64`.

Steam is installed from the CachyOS `steam-jupiter-stable` package, which provides the `steam` command. Discord and Spotify Launcher are available from the configured repositories. Spotify Launcher downloads the Spotify client the first time it is started.

## Build

Build on an Arch Linux system. The build profile depends on the CachyOS package repository and keyring, so configure that repository as shown in `.github/workflows/build.yml` before a local build.

Install the build tools:

```bash
sudo pacman -S --needed archiso mkinitcpio-archiso git squashfs-tools grub
```

Clone the project:

```bash
git clone https://github.com/RUTUJEKWIELKI/ZjebOS.git
cd ZjebOS
```

Build the desktop ISO:

```bash
sudo ./buildiso.sh -p desktop -v -w
```

The resulting ISO is written to the `out/desktop` directory. On every successful push to `master` (and on manual workflow dispatch), GitHub Actions also publishes the ISO and its SHA-256 checksum as a GitHub Release.

## Build options

```
./buildiso.sh -h
```

- `-c`: keep the existing work directory instead of cleaning it
- `-r`: enable building in RAM when more than 23 GB of RAM is available
- `-w`: remove the build directory after the ISO has been created
- `-p <profile>`: select the build profile (default: `desktop`)
- `-v`: enable verbose build output
