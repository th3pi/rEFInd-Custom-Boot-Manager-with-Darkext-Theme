# rEFInd - Custom Boot Manager

Status: Not started

## Installing rEFInd (USB Installation)

### Required Items

- [rEFInd.img](https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download) (Sourceforge.net)
- [Rufus](https://rufus.ie/) (Rufus.ie)
- [EasyUEFI](https://www.easyuefi.com/index-us.html) (EasyUEFI.com)
- [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) (mackie100projects.altervista.org)
- USB Flash Drive
- UUID of the volume rEFInd will be installed on (Need only if there are more than one volume with EFI partition on them)

### Installation steps

1. Getting the UUID

    ### Windows

    - Install EasyUEFI trial
    - Open it up, select Manage Boot Options
    - Select an EFI partition and get the **GPT partition GUID** — note it down somewhere

    ### MacOS

    - Open Clover Configurator
    - Find your EFI volume in Mount EFI under Tools section — note down the Disk UUID somewhere
2. Preparing the installation USB Flash Drive
    - Unzip the downloaded file refind zip file downloaded from Sourceforge — save the .img file somewhere convenient
    - Plug in USB Flash Drive
    - Open up Rufus and select the options accordingly:
        - Device: USB Flash Drive
        - Boot Selection: refind-flashdrive-0.12.0.img
        - Partition Scheme: GPT
        - Target System: BIOS or UEFI
        - Volume label: rEFInd Installation
        - File System: FAT32
        - Cluster Size: No change
        - Click Start — Once done reboot into BIOS and follow #2
3. Installing rEFInd into a HDD/SSD
    - From BIOS boot menu boot into the rEFInd USB Flash Drive
    - Once booted into rEFInd, select the first option on the second the row — should be **Install to a disk**
    - Match the GUID you jot down earlier. Navigate to it and press enter.
    - Done. Reboot into BIOS and make rEFInd your #1 Boot Option, to always boot into rEFInd by default

---

## Installing Darkext Theme

![Darkext Preview](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f9957e9a-9740-4111-8daf-a95677d66c45/rEFInd_Boot_Screen.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200408%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200408T223952Z&X-Amz-Expires=86400&X-Amz-Signature=c66dac86bc8bfbfbbce45475673064412740e566bd5cbf013a0257c5077396fa&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22rEFInd_Boot_Screen.png%22)

### MacOS

1. Download Clover Configurator
2. Mount EFI under Tools
    - Mount the EFI partition where rEFInd was installed
    - Click Open Partition
3. Clone or Download this repository
4. Create a new folder named **refind** in EFI > refind
5. Copy all the files (except icon templates folder, README.md, and screenshot.png) into the themes folder
6. Go back into the refind folder and add this line to the end of `refind.conf` 
    - `include themes/theme.conf`
