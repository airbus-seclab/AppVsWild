# AppVsWild - Challenge

## Context

This is the AppVsWild security challenge. AppVsWild is an application protection based on the [Ramooflax](https://github.com/sduverger/ramooflax) hypervisor.

The protection helps encrypted binaries to run seamlessly on an x86 hardware virtualisation equipped system. It's OS agnostic. For now, the provided toolchain only allow Linux 32 bits ELF binaries to be protected.

The protection has been presented during [SSTIC 2016](https://www.sstic.org/2016/presentation/app_vs_wild/). Please refer to the slides and article available on the website.

## Purpose

You have to retrieve the encrypted e-mail address and hash value distributed within the protected application, from the software perspective of the running operating system.

The challenge is delivered under the form of a VMware virtual machine provided with a hard disk drive booting Ramooflax and then booting a second hard drive that you have to add to the VM configuration.

That way, you will be able to run your own Linux 32 bits operating system with all of your hacking tools inside, root, ring 0 access, whatever you want to break into Ramooflax protection.

## Rules

Consider attacking the protection from the context of the virtual machine. The protection is aimed at protecting applications on remote hardware instances that you won't be able to access under normal conditions.

However, you are given the right to operate at ring 0 because you own the running operating system.

- you can't inspect the Ramooflax hard disk to tamper with Ramooflax hypervisor binary.
- you can't use VMware gdbstub to debug physical memory.
- you can't analyse VMware memory/disk files on your host.
- you can't backdoor SMM VMware bios.
- you can't use any VMware vulnerability.
- you can't change the boot chain (Ramooflax boots first then your Linux distribution boots).
- you can't use DMA (for now we do not implement I/O MMU).
- you can't take benefit of Ramooflax logs to the serial port.

Your solution won't be considered if not relevant with regard to these rules. Be fair, play the game. The goal is to break into Ramooflax, not VMware.

## Configuration

The VM has been tested under VMware Workstation 12 and Fusion 8. It does make use of Nested virtualization support. The VM only runs with a single core enabled.

For convenient hacking, we did not disable Ramooflax logs to the serial port (redirected to a file). At some point, your system might crash. Hey, this is an early stage proof of concept. At least you will have some info to discover what happened and feel free to restart the VM.

The VM is configured to boot on primary HDD with Ramooflax and Grub installed on it. The first Grub entry boots Ramooflax then restarts Grub. Choose the second entry to boot your added HDD. The bootloader of your HDD has to be installed in the MBR, else you may have to fix the Grub entry to boot a specific partition. You may also have to fix your linux kernel command line to give the correct ```root=/dev/sdxx```.

The VM comes with a network adapter in NAT mode.

## Obtain

You can download the virtual machine archive (~560 KB) [here](https://github.com/sduverger/AppVsWild/vm.tar.gz).
You can download the protected application (~3 KB) [here](https://github.com/sduverger/AppVsWild/app.gz).

Good Luck !

## Contact

stephane duverger - gmail
