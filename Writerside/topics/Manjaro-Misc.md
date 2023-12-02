# Manjaro Misc

[![manajaro-logo](manjaro_logo.png)](https://manjaro.org/)

## Build of Aur Package {collapsible="true" default-state="expanded"}

1. Ensure you have necessary files for building applications from source
    1. `pamac install base-devel git`
1. Clone the pkg build
    1. `git clone [url]`
1. Change directory to cloned folder
    1. `cd [folder]`
1. To make/compile the package run
    1. `makepkg -S`
1. List folder content
    1. `ls`
1. Upgrade package - file file ending .pkg.tar.zst and run
    1. `sudo pacman -U [file_name.pkg.tar.zst]`
    1. or `makepkg -i` (instead of `-U` flag)
    1. or `makepkg -is` (combines steps 4 & 6 together)

## Upgrade packages installed from Aur {collapsible="true" default-state="expanded"}

`pacman upgrade -a`

<seealso>
[User Guide](https://mirrors.gigenet.com/OSDN//storage/g/m/ma/manjaro/Manjaro-User-Guide.pdf) |
[Manjaro Forum](https://forum.manjaro.org/) |
[Manjaro Wiki](https://wiki.manjaro.org/index.php/Main_Page)
</seealso>
