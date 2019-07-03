# Running OS X(macOS) under Virtual Box

[![works badge](https://cdn.rawgit.com/nikku/works-on-my-machine/v0.2.0/badge.svg)](https://github.com/nikku/works-on-my-machine)

I didn't own this method at any way. I found this config in one of russian forums. 
PR me or write an issue, if you found some interesting things.

0. Remember: This is illegal to run macOS on non-Macintosh devices. So, fuck you Apple, for your licences! 
1. Create a VM for macOS. 
2. Check is EFI enabled.
3. Close VirtualBox. (really important, because VBox loads VM config once at start and rewriting it on close)
4. Open a folder with *.vbox. (must be in VirtualBox VM/<name>/<name>.vbox
5. Find <ExtraData> XML section.
6. Add these lines at the end of section. Before `</ExtraData>`
```
      <ExtraDataItem name="VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" value="Iloveapple"/>
      <ExtraDataItem name="VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" value="MacBookPro11,3"/>
      <ExtraDataItem name="VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" value="1.0"/>
      <ExtraDataItem name="VBoxInternal/Devices/smc/0/Config/DeviceKey" value="ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"/>
      <ExtraDataItem name="VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" value="1"/>
      <ExtraDataItem name="VBoxInternal2/EfiBootArgs" value="  "/> <!-- Use this to pass boot args to OSX -->
      <ExtraDataItem name="VBoxInternal2/EfiGraphicsResolution" value="1440x900" /> <!-- https://www.virtualbox.org/manual/ch03.html#efividmode -->
```
7. Convert installation CD to ISO. (don't use patched versions of OS)
8. Run VM and install it as usually. After installation you will have working macOS copy.

## Known Issues
* For some reason XCode didn't installing from AppStore. 
* Graphics are slow. Possible solution: Enable SSH and just login it from your host. CLI rocks here. (tell me how to disable graphics, please)
