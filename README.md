# AppVsWild - Challenge

## Context

This is the AppVsWild security challenge. AppVsWild is an application protection based on the [Ramooflax](https://github.com/sduverger/ramooflax) hypervisor.

The protection helps encrypted binaries to run seamlessly on an x86 hardware virtualisation equipped system. It's OS agnostic. For now, the provided toolchain only allow Linux 32 bits ELF binaries to be protected.

The protection has been presented during [SSTIC](https://www.sstic.org/2016/presentation/app_vs_wild/) 2016. Please refer to the slides and article available on the SSTIC website.

## Purpose

You have to retrieve the encrypted e-mail address and hash value distributed within the protected application, from the software perspective of the running operating system.

The challenge is delivered under the form of a VMWare virtual machine provided with a hard disk drive booting Ramooflax and then booting a second hard drive that you have to add to the VM configuration.

That way, you will be able to run your own Linux 32 bits operating system with all of your hacking tools inside, root, ring 0 access, whatever you want to break into Ramooflax protection.

## Obtain

You can download the virtual machine archive [here](https://github.com/sduverger/AppVsWild/vm.tar.gz).
You can download the protected application [here](https://github.com/sduverger/AppVsWild/app.gz).

## Rules

Consider attacking the protection from the context of the virtual machine. The protection is aimed at protecting applications on remote hardware instances that you won't be able to access under normal conditions.

However, you are given the right to operate at ring 0 because you own the running operating system.

- you can't inspect the ramooflax hard disk to tamper with Ramooflax hypervisor binary.
- you can't use VMware gdbstub to debug physical memory
- you can't analyse VMware memory/disk files on you host.
- you can't backdoor SMM VMware bios.
- you can't use any VMware vulnerability.

Your solution won't be considered if not relevant with regard to these rules.

I even give you the cryptographic material used to encrypt the binary. The goal is to break into Ramooflax, not VMware.


```
AES Key 6472779d30d18aa79fdce01a6ad497e6c7eb4dbff357c7899a8d22468211b4a7
```
```AES IV 0ae733b7a18c727f2bd5c9b778de5200
```
```HMAC Key 30019fef730d55589045d892bfda40e208761388c1cebce8fc336a7f2c940680
```



## Contact

stephane duverger - gmail
