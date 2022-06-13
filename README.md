<h1>macOS Monterey 12.4 on Dell Vostro 5468 using OpenCore 0.8.1</h1>

![Desktop Screenshot](https://user-images.githubusercontent.com/40514988/173263923-46426c7f-9726-4a6e-b95e-13af2f976f0e.png)

![About Mac](https://user-images.githubusercontent.com/40514988/173263980-82b4e496-53f5-45b1-9848-98ce10ab9fc1.png)

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
      <td>Airportitlwm</td>
      <td>2.2.0 - Alpha</td>
    </tr>
    <tr>
      <td>AppleALC</td>
      <td>1.7.2</td>
    </tr>
    <tr>
      <td>BrightnessKeys</td>
      <td>1.0.3</td>
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
      <td>1.5.9</td>
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Set to Factory Mode</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td>TPM</td>
      <td>Off</td>
    </tr>
    <tr>
      <td>Fastboot</td>
      <td>Minimal</td>
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

`Combojack` also needed for fix audio distortion after sleep with unplugged charger, (run install.sh)

When updating, in order to use VoodooI2C without issues, delete `VoodooInput.kext` from `VoodooPS2Controller.kext/Contents/PlugIns/`.

## More Screenshoots

![Hackintool](https://user-images.githubusercontent.com/40514988/173264013-8199b888-a585-4e59-b475-0c220282270b.png)

![Installed Kext](https://user-images.githubusercontent.com/40514988/173264018-1c2b2be9-a0a2-417f-939b-4a4b1c2c6047.png)

![USB Mapping](https://user-images.githubusercontent.com/40514988/173264027-78d80f57-3ca6-4b86-97ca-909a0aa213a5.png)

![PCIE](https://user-images.githubusercontent.com/40514988/173264040-eb0220c6-3792-4b62-944b-c14fcfe39e08.png)


## Changelog

##### 08/may/2022
Updated and Rebuild config to OpenCore 0.8.1

Updated And Cleanup Some Kext

Disabled ShowPicker and Cleanup Resources

##### 08/may/2022
Updated Airportitlwm to v2.2.0 - Alpha for fixing random kernel panics

Updated AppleALC to 1.7.1

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
