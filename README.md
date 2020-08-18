# homelab

## Adding more HDDs with SAS HBA (host bus adapter)

There's a number of affordable options
- LSI 9211 - the most general and recommended option
- IBM ServeRAID M1015/M1115
- Dell H310

## Cross flashing to a LSI9211-8i
https://linustechtips.com/main/topic/104425-flashing-an-lsi-9211-8i-raid-card-to-it-mode-for-zfssoftware-raid-tutorial/

https://www.servethehome.com/ibm-serveraid-m1015-part-4/

## General: Convert LSI9240(IBM M1015) to a LSI9211-IT mode

```
megarec -writesbr 0 sbrempty.bin
megarec -cleanflash 0
<reboot, back to USB stick >
sas2flsh -o -f 2118it.bin -b mptsas2.rom (sas2flsh -o -f 2118it.bin if OptionROM is not needed)
sas2flsh -o -sasadd 500605bxxxxxxxxx (x= numbers for SAS address)
<reboot>
```
Done!

### Linux

### UEFI

## Tweaks [1][servethehome-com-ibm-serveraid-m1015]
Of possible use to ZFS fanatics, when flashing the card to IT mode, do not flash the mptsas2.rom, this then will not load the boot BIOS
Any SAS or SATA IIIdrives added will just passthrough as normal, as there is nothing to see or do in the BIOS in IT mode, you may as well not load it. This makes boot and reboot time faster as it doesn’t have to load the BIOS and wait for a key press. BUT you will need it if you are booting from one of the drives attached to the IBM M1015. You will also need it if you are running IR mode to access to the BIOS to setup RAID functions. This might be of use to some users.

## Downloads

## References

[servethehome-com-ibm-serveraid-m1015]: https://www.servethehome.com/ibm-serveraid-m1015-part-4/ servethehome.com/ibm-serveraid-m1015-part-4


