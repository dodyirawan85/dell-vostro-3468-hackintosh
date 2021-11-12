<h1>macOS Monterey on Dell Vostro 5468 using OpenCore 0.7.5</h1>

![Desktop Screenshot](https://user-images.githubusercontent.com/40514988/140243848-203fd15b-d141-4fe2-b095-3bc763569299.png)

![About Mac](https://user-images.githubusercontent.com/40514988/140243924-a3c20205-5b3c-4d5d-ba78-bdca13c55cdc.png)


## Important

This repo has a lot of things specific to my laptop, for example all the ACPI tables. It should work in a identic laptop, but maybe it won't.

## Instructions

You **must** add your own serialnumber. I recommend [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS). Remember to use `MacBookPro14,1`. 

Use this a a starting point, this is no replacement of your own research, trial and error.

## What is working

### Completely supported

#### CPU

XCPM power management is native supported. HWP is fully enabled as well.

#### Wi-Fi & Bluetooth

This laptop comes with an Intel WiFi + Bluetooth combo.

#### Camera

Camera is functioning normally.

#### USB

USB ports are working as expected.

Use USBInject-All.kext then with Hackintool disable all unused ports and generate a USBPorts.kext

#### Ethernet

Functioning normally.

#### Display and External Monitors

Working fine with hardware acceleration. External monitors work fine with HDMI or VGA.

#### Battery

Detected and correct values.

#### Sensors

Fan Speed, CPU temp and voltage.

#### Touchpad

Functioning with multigestures.

#### Keyboard

Brightness keys works perfectly

### Need more testing

#### Audio

Audio on speakers and headphones.

#### Sleep and Wake

Sometimes weird behavior happens. Example, if a key if pressed when the laptop is waking up from sleep, the keyboard will stop responding, and the key pressed will repeat indefinitely in the password field, the touchpad also dies.

A workaround i've found is when the laptop wakes from sleep, do not press any key inmediately. Wait 5-10 seconds then start typing, that works for me, but sometimes the touchpad just quits anyway.

### Not Tested

#### Others

Internal SD card Reader


## Additional info, quirks, findings, etc 

`CtlnaAHCIPort` is absolutely necesary to Big Sur. Using `MinKernel` this kext only loads in Big Sur and above

`IntelBluetoothInjector.kext` only load below Big Sur (using `MaxKernel` = `20.99.9`). This kext makes Monterey unable to boot.

Use `BlueToolFixup` from `BrcmPatchRAM` for bluetooth fix in Monterey

When updating, in order to use VoodooI2C without issues, delete `VoodooInput.kext` from `VoodooPS2Controller.kext/Contents/PlugIns/`.

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
      <td>VGA</td>
      <td>Intel HD Graphics 620</td>
    </tr>
    <tr>
      <td>Audio</td>
      <td>Realtek ALC256 (layout-id: 21)</td>
    </tr>
    <tr>
    </tr>
  </tbody>
</table>


![Hackintool](https://user-images.githubusercontent.com/40514988/140244023-b2f295e1-6db5-469a-9e91-558ca13fbc3d.png)

![Installed Kext](https://user-images.githubusercontent.com/40514988/140244055-ed115da1-59e5-496b-a7d6-b0d68b4d5e85.png)

![PCIE List](https://user-images.githubusercontent.com/40514988/140244075-083bdb38-7551-43f1-82e7-59eb66f76fe3.png)

## Changelog

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
