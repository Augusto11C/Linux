






1. Hard Drive Naming Convention: The first thing you need to know is this: There’s no C or D drive in Linux. There are equivalents, but when you come across a reference to a hard drive in Linux, you’ll typically see something like /dev/sda, /dev/sdb, /dev/sdc, … etc. The “dev” is short for device, and, in this case, a block storage device. The “sd” is short for SCSI mass-storage driver. (SCSI stands for Small Computer System Interface.) For the rest of this article, the “/dev/” part will be dropped, so all references to hard drives (and partitions) will start with the last part only. 


2. Partition Tables: In simple terms, a partition table describes the layout of partitions of a hard drive. There are two partition table standards – MBR (Master Boot Record) and GPT (GUID Partition Table). MBR, also know as ms-dos, is what you might call the first standard. GPT came much later. 

The MBR partitioning scheme is found on older computers. Newer computers support both schemes, so it’s still possible to use an MBR partitioning scheme on those computers. MBR’s major limitations led to the development of GPT. Those limitations are:

    - It does not allow the configuration of more than four main partitions. Those partitions are called primary partitions.
    - Disk partitions are limited to 2TB

Newer computers come with a replacement firmware for the old BIOS system called UEFI (Unified Extensible Firmware interface), and GPT is a part of the UEFI standard.   


3. **Partitions and Partition Numbering:** To install an operating system on a hard drive, it must first be subdivided into distinct storage units. Those storage units are called **partitions**.

**MBR**
Under the MBR partitioning scheme, there are three different types of partitions – Primary, Extended, and Logical. 

With MBR, any partition that is not explicitly created as an extended or logical partition, is a primary partition and there can be no more than four primary partitions.

> Type: if you attempt to create another partition using the free space, the installer will throw up the type of error message

To get around the four primary partition limitation of MBR it is possible **tagging a partition as an extended partition**, it is then possible to create many more partitions under it. Those partitions are called logical partitions. Theoretically, there is no limit to the number of logical partitions that you can create.

**GPT**
GPT overcomes two limitations of the MBR scheme – maximum of four primary partitions, and the 2 TB limit to partition sizes. With GPT, there can always be unallocated space at the end of existing partitions. And unlike in MBR, that “free space” can be used to create additional partitions


4. **File Systems:** Before a disk partition can be used to store data, it must first be formatted. The formatting process includes stamping it with a file system. The file system on Windows is NTFS (New Technology File System).

in Linux, there are more than one file systems available.

> File systems supported by linyx: Btrfs is a new file system which is an enhanced version of Ext4. Ext4, in turn, which is an enhanced version of Ext3, is the default on recent releases. Ext3, in turn, is an enhanced version of Ext2.

**Swap Partition**
Swap is a small section of unformatted hard drive that Linux and other operating systems use as virtual memory. It’s a method of increasing the amount of total RAM (Physical RAM + virtual memory). And it is a given that your distribution will set up a small amount of hard drive as swap space. 

5. **Mount Points:** Assigning a mount point to a partition is one of the things that comes with formatting it. A Linux desktop, the most commonly used mount points are /, /boot, /home, and swap.


## How to install Ubuntu on a GPT partition table without using EFI boot?
[How to install Ubuntu on a GPT partition table without using EFI boot?](https://askubuntu.com/questions/731740/how-to-install-ubuntu-on-a-gpt-partition-table-without-using-efi-boot)