# Instructions

These instructions explain how to set up the tools required to build **shiningcrystal**, including [**rgbds**](https://github.com/gbdev/rgbds), which assembles the source files into a ROM.

If you run into trouble, ask for help on IRC or Discord (see [README.md](README.md)).


## Windows 10

Download and install [**Windows Subsystem for Linux**](https://docs.microsoft.com/en-us/windows/wsl/install-win10). Then open the **WSL terminal**.

Update WSL's software before continuing. If you chose Debian, Ubuntu, or another distribution that uses `apt-get`, then enter this command:

```bash
apt-get update && apt-get upgrade
```

WSL has its own file system that's accessible from Windows, but it's kind of a pain. Windows files *are* accessible from WSL, though. So you're going to want to install shiningcrystal within Windows. You'll have to change the **current working directory** every time you open WSL.

For example, if you want to store shiningcrystal in **C:\Users\\*\<user>*\Desktop**, enter this command:

```bash
cd /mnt/c/Users/<user>/Desktop
```

(The Windows `C:\` drive is called `/mnt/c/` in WSL. Replace *\<user>* in the example path with your username.)

If this works, then follow [the instructions for **Linux**](#linux) below for whatever distribution you installed for WSL.

Otherwise, continue reading below for [the older Windows instructions](#windows).


## Windows

Download [**Cygwin**](http://cygwin.com/install.html): **setup-x86_64.exe** for 64-bit Windows, **setup-x86.exe** for 32-bit.

Run setup and leave the default settings. At the "**Select Packages**" step, choose to install the following, all of which are in the "**Devel**" category:

- `make`
- `git`
- `gcc-core`

Double click on the text that says "**Skip**" next to each package to select the most recent version to install.

Then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/windows) for Windows with Cygwin to install **rgbds 0.5.0**.

**Note:** If you already have an older rgbds, you will need to update to 0.5.0. Ignore this if you have never installed rgbds before. If a version newer than 0.5.0 does not work, try downloading 0.5.0.

Now open the **Cygwin terminal** and enter the following commands.

Cygwin has its own file system that's within Windows, at **C:\cygwin64\home\\*\<user>***. If you don't want to store shiningcrystal there, you'll have to change the **current working directory** every time you open Cygwin.

For example, if you want to store shiningcrystal in **C:\Users\\*\<user>*\Desktop**:

```bash
cd /cygdrive/c/Users/<user>/Desktop
```

(The Windows `C:\` drive is called `/cygdrive/c/` in Cygwin. Replace *\<user>* in the example path with your username.)

Now you're ready to [build **shiningcrystal**](#build-shiningcrystal).


## macOS

Install [**Homebrew**](https://brew.sh/). Follow the official instructions.

Open **Terminal** and prepare to enter commands.

Then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/macos) for macOS to install **rgbds 0.5.0**.

Now you're ready to [build **shiningcrystal**](#build-shiningcrystal).


## Linux

Open **Terminal** and enter the following commands, depending on which distro you're using.

### Debian or Ubuntu

To install the software required for **shiningcrystal**:

```bash
sudo apt-get install make gcc git
```

Then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/source) to build **rgbds 0.5.0** from source.

### OpenSUSE

To install the software required for **shiningcrystal**:

```bash
sudo zypper install make gcc git
```

Then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/source) to build **rgbds 0.5.0** from source.

### Arch Linux

To install the software required for **shiningcrystal**:

```bash
sudo pacman -S make gcc git rgbds
```

Then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/arch) for Arch Linux to install **rgbds 0.5.0**.

If you want to compile and install **rgbds** yourself instead, then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/source) to build **rgbds 0.5.0** from source.

### Termux

To install the software required for **shiningcrystal**:

```bash
sudo apt install make clang git sed
```

To install **rgbds**:

```bash
sudo apt install rgbds
```

If you want to compile and install **rgbds** yourself instead, then follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/source) to build **rgbds 0.5.0** from source.

### Other distros

If your distro is not listed here, try to find the required software in its repositories:

- `make`
- `gcc` (or `clang`)
- `git`
- `rgbds`

If `rgbds` is not available, you'll need to follow the [**rgbds** instructions](https://rgbds.gbdev.io/install/source) to build **rgbds 0.5.0** from source.

Now you're ready to [build **shiningcrystal**](#build-shiningcrystal).


## Build shiningcrystal

To download the **shiningcrystal** source files:

```bash
git clone https://github.com/ShiningCrystal-Team/shiningcrystal
cd shiningcrystal
```

To build **pokecrystal.gbc**:

```bash
make
```

To build **pokecrystal11.gbc**:

```bash
make crystal11
```

### Build with a local rgbds version

If you have different projects that require different versions of `rgbds`, it might not be convenient to install rgbds 0.5.0 globally. Instead, you can put its files in a directory within pokecrystal, such as `pokecrystal/rgbds-0.5.0/`. Then specify it when you run `make`:

```bash
make RGBDS=rgbds-0.5.0/
```

```bash
make RGBDS=rgbds-0.5.0/ crystal11
```
