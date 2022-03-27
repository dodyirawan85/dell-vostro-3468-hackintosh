<h1>macOS BigSur 11.6.5 on Dell Vostro 5468 using OpenCore 0.7.9</h1>

![Desktop Screenshot](https://user-images.githubusercontent.com/40514988/148590344-9d919ee1-88ad-4f2e-a4e0-598b5f5c821e.png)

![About Mac](https://user-images.githubusercontent.com/40514988/148592751-1295af57-d02b-46d0-a0de-67f79798b784.png)


<h2>Laptop Specs</h2>
<table>
  <thead>
    <tr>
      <td style="text-align: center">Feature</td>
      <td style="text-align: center">Specification</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Model</td>
      <td>Dell Vostro 5468</td>
    </tr>
    <tr>
      <td>Processor type</td>
      <td>Intel Core i3-7100U</td>
    </tr>
    <tr>
      <td>RAM</td>
      <td>8+8 Dual Channel DDR4 2133 MHz</td>
    </tr>
    <tr>
      <td>Storage</td>
      <td>M.2 Sata 512GB + 1TB Sata HDD</td>
    </tr>
     <tr>
      <td>VGA</td>
      <td>Intel HD Graphics 620</td>
    </tr>
    <tr>
      <td>Audio</td>
      <td>Realtek ALC256 (layout-id: 21)</td>
    </tr>
    <tr>
      <td>Wifi Card</td>
      <td>Intel® Dual Band Wireless-AC 3165</td>
    </tr>
    <tr>
      <td>Touchpad</td>
      <td>Dell I2C</td>
    </tr>
  </tbody>
</table>

<h2>Kext Info</h2>
<table>
  <thead>
    <tr>
      <td style="text-align: center">Name</td>
      <td style="text-align: center">Version</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>AppleALC</td>
      <td>1.7.0</td>
    </tr>
    <tr>
      <td>BrightnessKeys</td>
      <td>1.0.2</td>
    </tr>
    <tr>
      <td>ECEnabler</td>
      <td>1.0.2</td>
    </tr>
    <tr>
      <td>IntelBluetoothFirmware</td>
      <td>2.1.0</td>
    </tr>
     <tr>
      <td>Lilu</td>
      <td>1.6.0</td>
    </tr>
    <tr>
      <td>RealtekRTL8111</td>
      <td>2.4.2</td>
    </tr>
    <tr>
      <td>RestrictEvents</td>
      <td>1.0.7</td>
    </tr>
    <tr>
      <td>VirtualSMC</td>
      <td>1.2.9</td>
    </tr>
    <tr>
      <td>VoodooI2C</td>
      <td>2.7</td>
    </tr>
    <tr>
      <td>VoodooPS2Controller</td>
      <td>2.2.8</td>
    </tr>
    <tr>
      <td>WhateverGreen</td>
      <td>1.5.8</td>
    </tr>
    <tr>
      <td>Others</td>
      <td>Generated Using SSDTime</td>
    </tr>
  </tbody>
</table>

<h2>Bios Settings</h2>
<table>
  <thead>
    <tr>
      <td style="text-align: center">Name</td>
      <td style="text-align: center">Value</td>
      <td style="text-align: center">Comment</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Set to Factory Mode</td>
      <td>Yes</td>
      <td>-</td>
    </tr>
  </tbody>
</table>

## Important

This repo has a lot of things specific to my laptop, for example all the ACPI tables. It should work in a identic laptop, but maybe it won't. You can also run monterey, but for some reaseon i'll stick to bigsur for better experience

## Instructions

You **must** add your own serialnumber. I recommend [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS). Remember to use `MacBookPro14,1`. 

Use this a a starting point, this is no replacement of your own research, trial and error.

## What is working

### Completely supported

#### Audio

Audio on speakers and headphones.

#### CPU

XCPM power management is native supported. HWP is fully enabled as well.

#### Wi-Fi & Bluetooth

This laptop comes with an Intel WiFi + Bluetooth combo.

#### Camera

Camera is functioning normally.

#### USB

USB ports are working as expected.

Use USBInject-All.kext then with Hackintool disable all unused ports and generate a SSDT-UIAC.aml and SSDT-USBX.aml

#### Ethernet

Functioning normally.

#### Display and External Monitors

Working fine with hardware acceleration. External monitors work fine with HDMI or VGA.

#### Battery

Detected and correct values.

#### Sensors

Fan Speed, CPU temp and voltage.

#### Sleep and Wake

Now working perfect

#### Touchpad

Functioning with multigestures.

#### Keyboard

Brightness keys works perfectly

### Not Tested

Internal SD card Reader


## Additional info, quirks, findings, etc 

`CtlnaAHCIPort` is absolutely necesary to Big Sur+.

`IntelBluetoothInjector.kext` only load in Big Sur and below. Set `MaxKernel` to `20.99.9` for booting in monterey or just remove it if you only use monterey.

`BlueToolFixup` from `BrcmPatchRAM` needed for bluetooth fix in Monterey

`Airportitlwm` needed to updated for monterey if you want to

`Combojack` also needed for fix audio distortion after sleep with unplugged charger, (run install.sh)

When updating, in order to use VoodooI2C without issues, delete `VoodooInput.kext` from `VoodooPS2Controller.kext/Contents/PlugIns/`.


![Hackintool](https://user-images.githubusercontent.com/40514988/148591123-c8fc0f44-cf25-4a24-bdd7-36da01737806.png)

![Installed Kext](https://user-images.githubusercontent.com/40514988/148591199-df389bb6-5755-469a-a0aa-79f6933caa12.png)

![PCIe](https://user-images.githubusercontent.com/40514988/148591266-22d13fcd-c0f2-48c5-ae39-b8bc0120aa2f.png)

## Changelog

##### 27/mar/2022
Updated and Rebuild config to OpenCore 0.7.9

Updated kext

Updated ssdt

##### 08/jan/2022:

Updated and Rebuild config to OpenCore 0.7.6

Updated kexts

Updated generated ssdt

Added compiled and decompiled dsdt

Added `-vi2c-force-polling` to bootargs for better touchpad response

Added OpenCore Resource for gui

Drop unused kext

Fixed Audio Distortion After Sleep

##### 13/nov/2021:

Fixed brightness key

Added cpufriend

Change graphics AAPL,ig-platform-id (Better performance)

And more

##### 04/nov/2021:

Update to OpenCore 0.7.5

Update to Monterey

Added SSDT-HPET.aml for fixing irq conflicts

##### 23/oct/2021:

First Release
