# Boot virtual machine images on real hardware (Proof of Concept)

In early userspace (initramfs), mount a VM image as the new root and let
the boot process `switch_root` to it.

You can package `qemu-nbd` (from `qemu`), `mount.ntfs` (from `ntfs-3g`),
`losetup` (from `util-linux`) and various tools into the initramfs
for your mounting needs, so theoretically any format of root filesystem
images can be used.

## Known issues

- You must manually keep the host kernel and VM image kernel version in sync.
  Otherwise, kernel modules will fail to be found,
  resulting in missing drivers.

