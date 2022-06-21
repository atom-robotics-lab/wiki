# Ubuntu

## What is Ubuntu?
Ubuntu is a popular Linux distribution open-source operating system that’s operated by Canonical. Canonical supplies support and security updates for every release of Ubuntu and oversees its ongoing development. Ubuntu has multiple editions, including core, server, and desktop, that allow it to run across different types of machines. It can be used on personal computers, servers, supercomputers, in cloud computing, and more.

## Why use Ubuntu?
Ubuntu is popular for a variety of reasons, and it’s attractive to builders who need a free, open source solution that’s secure and easy to use. The popularity of the software combined with the collaborative nature of open source means that Ubuntu is well-supported in the Canonical community. The operating system is user-friendly and customizable, and Ubuntu offers enhanced security within its OS.

# Installation of Ubuntu

## Prerequisites
- ### System requirements (recommended):
    - 2 GHz dual-core processor
    - 4GB memory
    - 25GB available disk space for storage (less if installing the minimal version)
    - DVD drive or USB port
    
- At least a 8GB USB drive

## Step 1: Download the Installation Media

1. In a web browser, visit the [Ubuntu download](https://ubuntu.com/download) page and pick the Ubuntu version suitable for your machine. The most popular versions include:
    - [Ubuntu Desktop](https://ubuntu.com/download/desktop)
    - [Ubuntu Server](https://ubuntu.com/download/server)
    - [Ubuntu Derivatives](https://ubuntu.com/desktop/flavours)

2. Once you find the version you need, click the green <b>Download button</b>. You’ll be taken to a thank-you page, and your download should start. (We will download and install Ubuntu 20.04 for desktops.)

    The download is an<b> .iso</b> file. You can use it to create a bootable USB drive.

3. Save the file to the location of your choice.

        Note: If you’re installing to a virtual machine (like VirtualBox), you can mount the .iso image directly. In such case you can skip the steps -

## Step 2: Create Bootable USB
You will need a USB drive with 4GB or more. <b>This process will delete all data on the USB drive</b>. Make sure to backup any existing data on the USB drive.

### Option 1: Create a Bootable USB Drive on Ubuntu
Use the <b>Create startup disk</b> tool:

1. Open a search dialog, and type create startup.
2. If it’s not installed, the Software Center will offer the option to install it – choose the option for USB drive, then open the utility.
3. In the top pane, click Other, then browse and select the Ubuntu 20.04 .iso file you downloaded.
4. In the bottom pane, select your USB drive.
5. Click Make startup disk.

### Option 2: Create a Bootable USB Drive on Windows

You’ll need to install a third-party utility called Rufus to create a USB bootable drive.

1. Download the [Rufus utility](https://rufus.ie/en/). Scroll down to the download section and click the link to download the latest version of Rufus.
<br>
<iframe
    width="369"
    height="206"
    src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/download-rufus.png"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen

</iframe>

2. Run the file once downloaded.

3. A pop-up dialog opens. You will be prompted whether you want to check for online updates. Select <b> No</b>.

<br>
<iframe
    width="369"
    height="120"
    src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/launch-rufus.png"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen

</iframe>

4. The Rufus utility launches. Plug in the USB drive – you should see the drive pop up in the device field.

- Set the USB as the device you wish to write to
- In the Boot Selection drop-down, click <b> Disk or ISO image</b>. 
- CLick the <b> Select </b> button to the right.
- Browse and select the .iso ubuntu file you downloaded earlier.

<br>
<iframe
    width="369"
    height="471"
    src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/launch-rufus.png"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen

</iframe>

5. Click <b> Start </b>

## Step 3: Boot up Ubuntu from USB
1. Turn off your system. Make sure you remove all other USB devices, such as printers, memory cards, etc.

2. Insert the Ubuntu USB drive into the system and turn on your machine.

There are two possible scenarios:

- The computer boots the USB drive automatically.
- You need to manually configure USB booting in the Boot Menu or BIOS/UEFI.
3. To manually configure the boot order, tap the boot menu key about once or twice per second as soon as the computer powers on.

The boot menu key may be different depending on your computer manufacturer. Below is a list of common boot keys associated to a brand:
<pre>
Asus                F8 or Esc<br>
Acer	            F12, F9 or Esc<br>
Compaq	            F9 or Esc<br>
Dell	            F12<br>
eMachines	        F12<br>
Fujitsu	            F12<br>
HP	                F9 or Esc<br>
Lenovo	            F8, F10 or F12<br>
Samsung	            F2, F12 or Esc<br>
Toshiba	            F12</pre>
4. Once you see your boot menu, use the arrows to pick the Ubuntu media to boot from. For a DVD, the entry will usually have DVD or Optical in the name. USB is usually labeled USB.

Your system should start loading the Ubuntu live disc menu.

Note: If you are experiencing issues when booting the USB from the boot menu, try to [boot the USB from BIOS/UEFI](https://phoenixnap.com/kb/how-to-install-ubuntu-18-04#ftoc-heading-5).

## Step 4: Run Ubuntu
You can test Ubuntu 20.04 before you commit to installing it. The .iso includes a live mode that only runs in memory.

Launch this mode by clicking *Try Ubuntu*.
<br>
<iframe
    width="369"
    height="164"
    src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/try-ubuntu-20.04.png"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen

</iframe>

## Step 5: Install Ubuntu 20.04 LTS Desktop
To begin the installation, click Install Ubuntu.

<br>
<iframe
    width="369"
    height="164"
    src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/install-ubuntu-20.04.png"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen

</iframe>

## Choose Keyboard Layout
By default, the system will select English and English.

If you have a non-standard keyboard, you can select it in the list. Alternately, click <b>Detect Keyboard Layout</b> and the system will automatically choose your keyboard. If you need to test your keyboard, use the labeled field.

When you’re ready, click <b>Continue</b>.

## Choose Starting Applications
- <b>Normal Installation</b> – This is the full Ubuntu Desktop experience, with office software, games, and media players.
- <b>Minimal Installation</b> – Choose this to save disk space, especially if you won’t be using media players or productivity software.

You’ll also be asked to confirm other options:

- <b>Download updates while installing Ubuntu </b>– This does the work of downloading large package files during the installation. Once the installation finishes, the packages will be ready to apply as updates.
- <b>Install third-party xsoftware for graphics and Wi-Fi hardware and additional media formats</b> – Some hardware, like graphics cards and wi-fi cards, do not have open-source driver support. Also, some media formats, such as .wmv, do not fall under the GPL license. If you need support for these, you’ll need to agree to additional terms of use.

## Disk Partitioning
Next, you’ll be presented with an <b>Installation Type</b> dialog. You can wipe the hard drive clean prior to installing Ubuntu by clicking <b>Erase disk and install Ubuntu</b>. If you go this route, skip ahead to the next step.

Advanced users may want to edit Advanced Features. Use this to specify your own disk partitions or set other advanced options:

- <b>Use LVM with the new Ubuntu installation</b>: LVM stands for Logical Volume Management. This is a tool for dynamically managing different virtual drives on your system. It’s much like an enhanced version of the gparted tool.
- Encrypt the new Ubuntu installation for security: This will encrypt the drive’s contents. You’ll choose a security key, which will be required to decrypt and use the drive.
- Experimental: Erase disk and use ZFS:  ZFS refers to Zettabyte File System, but it has grown into a hybrid file system and volume manager. Since it’s still being tested, avoid this setting on mission-critical production systems.
If you’d rather create your own hard drive partitions, click <b>Something Else</b>.

The next screen will allow you to create your own partition table and logical drives. This lets you divide a physical hard drive into different partitions. The operating system sees partitions as individual drives.

    Note: Some users create their /home directory on a separate partition. If the operating system needs to be reinstalled, the partition with the /home directory is unaffected.

Click<b> Continue</b> to apply your changes to the drive partitions.

You’ll be asked to <b>Write changes to disks</b>?  None of the options you’ve selected are permanent until you click <b>Continue</b> on this screen.  Click<b> Continue</b> to proceed.

## Select Time Zone
Once the system formats the disk partitions, the installer will ask Where are you?

Type the nearest large city into the box, and the system will set your local time zone.

Click <b>Continue</b>.

## Create User Account
Next, you’ll need to configure a user account. Fill in the following fields:
<pre>
Name:                   Your actual name.
Computer name:          This is the hostname or network name.
Username:               The user account name you want to use.
Password:               Enter and confirm a strong password – the installer will automatically evaluate your password strength.
Log in automatically:   This is not recommended for publicly accessible servers.
Require my password to log in: This is recommended for publicly accessible servers.</pre>
Click<b> Continue</b> to install Ubuntu.

Once the installer finishes, remove the Ubuntu installation media. You’ll be prompted to <b>Restart Now</b>.

### The system should boot into your fresh install of Ubuntu 20.04.
