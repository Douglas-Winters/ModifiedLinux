# Modified Arch Linux Kernel
---
Arch Linux, but with some additional modules added/built-in.

| Config Option | Name | Default Value | New Value | Description (Reason) |
| ------------- | ---- | ------------- | --------- | -------------------- |
| CONFIG_KVM | Kernel-based Virtual Machine (KVM) support | Module | Built-In | Removes the need for additional `kvm` option in initramfs/modprobe |
| CONFIG_KVM_INTEL | KVM for Intel (and compatible) processors support | Module | Built-In | Removes the need for additional `kvm-intel` option in initramfs/modprobe |
| CONFIG_KVM_AMD | KVM for AMD processors support | Module | Built-In | Removes the need for additional `kvm-amd` option in initramfs/modprobe |
| CONFIG_ACORN_PARTITION | Acorn partition support | Disabled | Enabled (Including all suboptions) | Adds support for devices formatted under Acorn operating systems |
| CONFIG_OSF_PARTITION | Alpha OSF partition support | Disabled | Enabled | Adds support for devices partitioned on an Alpha machine |
| CONFIG_AMIGA_PARTITION | Amiga partition table support | Disabled | Enabled | Adds support for devices partitioned under AmigaOS |
| CONFIG_ATARI_PARTITION | Atari partition table support | Disabled | Enabled | Adds support for devices partitioned under the Atari OS |
| CONFIG_UNIXWARE_DISKLABEL | Unixware slices support | Disabled | Enabled | Adds support for devices partitioned with UnixWare |
| CONFIG_SGI_PARTITION | SGI partition support | Disabled | Enabled | Adds support for devices partitioned with an SGI machine |
| CONFIG_ULTRIX_PARTITION | Ultrix partition tables support | Disabled | Enabled | Adds support for the partition table used by DEC (now Compaq) Ultrix machines |
| CONFIG_SUN_PARTITION | Sun partition tables support | Disabled | Enabled | Adds support for devices used by SunOS |
| CONFIG_SYSV68_PARTITION | SYSV68 partition table support | Disabled | Enabled | Adds support for devices used by Motorola Delta machines using sysv68 |
| CONFIG_CMDLINE_PARTITION | Command line partition support | Disabled | Enabled | Allows user to read partition table from bootargs |
| CONFIG_EXT4_FS | The Extended 4 (ext4) filesystem | Module | Built-In | Adds support for the ext4 file system |
| CONFIG_JFS_FS | JFS filesystem support | Module | Built-In | Adds support for IBM's Journaled Filesystem |
| CONFIG_XFS_FS | XFS filesystem support | Module | Built-In | Adds support for the XFS filesystem |
| CONFIG_GFS2_FS | GFS2 file system support | Module | Built-In | Adds support for the GFS2 filesystem | 
| CONFIG_OCFS2_FS | OCFS2 file system support | Module | Built-In | Adds support for the OCFS2 filesystem |
| CONFIG_BTRFS_FS | Btrfs filesystem support | Module | Built-In | Adds support for the Btrfs filesystem |
| CONFIG_NILFS2_FS | NILFS2 file system support | Module | Built-In | Adds support for the NILFS2 filesystem |
| CONFIG_F2FS_FS | F2FS filesystem support | Module | Built-In | Adds support for the F2FS filesystem |
| CONFIG_ZONEFS_FS | zonefs filesystem support | Module | Built-In | Adds support for the zonefs filesystem |
| CONFIG_ISO9660_FS | ISO 9660 CDROM file system support | Module | Built-In | Builds support for the standard CD-ROM filesystem directly into the kernel |
| CONFIG_UDF_FS | UDF file system support | Module | Built-In | Builds support for UDF file system directly into the kernel |
| CONFIG_MSDOS_FS | MSDOS fs support | Module | Built-In | Builds MS-DOS filesystem support into the kernel |
| CONFIG_VFAT_FS | VFAT (Windows-95) fs support | Module | Built-In | Builds Windows 95 filesystem support into the kernel |
| CONFIG_EXFAT_FS | exFAT filesystem support | Module | Built-In | Builds exFAT filesystem support into the kernel |
| CONFIG_NTFS3_FS | NTFS Read-Write file system support | Module | Built-In | Builds NTFS support into the kernel with the ability to read AND write |
| CONFIG_AFFS_FS | Amiga FFS file system support | Module | Built-In | Builds FFS support into the kernel |
| CONFIG_HFS_FS | Apple Macintosh file system support | Module | Built-In | Adds support to mount Mac-formatted floppy disks |
| CONFIG_HFSPLUS_FS | Apple Extended HFS file system support | Module | Built-In | Adds support to mount Mac-formatted hard drive partitions with full RW access |
| CONFIG_MINIX_FS | Minix file system support | Module | Built-In | Adds support for the minix file system |
| CONFIG_HPFS_FS | OS/2 HPFS file system support | Disabled | Built-In | Adds support to mount IBM OS/2 HPFS partitions |
| CONFIG_SYSV_FS | System V/Xenix/V7/Coherent file system support | Disabled | Built-In | Adds support to mount and Read-Write SysV filesystems |
| Native Language Support | | Only `NLS UTF-8` | All options Built-In | Adds support for all available locales in the filesystem |

---
# Build instructions

To build the kernel, you will need the following dependancies:
- coreutils
- bc
- cpio
- gettext
- libelf
- pahole
- perl
- python
- tar
- xz
- graphviz
- imagemagick
- python-sphinx
- python-yaml
- texlive-latexextra
- base-devel
- devtools

To build the package files, run the following command:
```
$ makepkg
```
To install the dependancies automatically, add `-s`:
```
$ makepkg -s
```
**Note that the build process will take anywhere from 15 minutes to over an hour, depending on your CPU speed and capabilities. My computer took 27 minutes to build**

---
After make has finished, you'll see two new files in the build directory. `linux-douglas-6.8.5.arch1-1-x86_64.pkg.tar.zst` and `linux-douglas-headers-6.8.5.arch1-1-x86_64.pkg.tar.zst`.
To install the kernel and headers, run the following command as root:
```
# pacman -U linux-douglas-6.8.5.arch1-1-x86_64.pkg.tar.zst linux-douglas-headers-6.8.5.arch1-1-x86_64.pkg.tar.zst
```
There is an additional package called `linux-douglas-docs-6.8.5.arch1-1-x86_64.pkg.tar.zst`. You can install that too if you want documentation.
