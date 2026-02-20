# Chai45HE

Chai45HE is a 40% Hall-effect keyboard based on the [HE60](https://github.com/peppapighs/HE60) project. This is a modified version that adapts the original 60% design to a compact 40% layout.

## Key Features

- 40% compact layout
- Hall-effect magnetic switches support
- Based on HE60's proven design and technology
- Custom PCB design files included

## ファームウェアの書き込み方法

1. [firmware.bin](firmware/firmware.bin) をダウンロードします。
2. 基板裏側の **BOOT** ボタンを長押ししながらUSBケーブルを接続し、Bootloader Modeに入ります。
3. [WebDFU](https://devanlai.github.io/webdfu/dfu-util/) にアクセスし、**DFU in FS mode** に接続します。
4. **Firmware Download** セクションでダウンロードした `firmware.bin` ファイルを選択します。
5. **Download** ボタンを押して書き込みを実行します。

## キー設定ガイド

### Tap-Holdの設定方法

Tap-Holdを使うと、短押し(Tap)と長押し(Hold)で異なるキーを割り当てることができます。

1. Remapで **Tap** に設定したいキーを配置します。
2. **Advanced Keys** から **Tap-Hold** を選択します。
3. **Hold** に設定したいキーを選択し、**Continue** を押します。
4. Hold用のキーを設定して **Done** で設定完了です。

### !@#$%などの記号キーの設定方法

Shiftキーとの組み合わせで入力される記号(!@#$%など)を単独のキーとして設定する方法です。

1. Remapで `1 2 3 4 5` を、`! @ # $ %` を入力したいキーに設定します。
2. **Advanced Keys** から **Dynamic Keystroke** を選択します。
3. 下の画像のようにShiftを割り当てます。

   ![Dynamic Keystrokeの設定例](/doc/dynamic-keystroke.png)

4. **Done** で設定完了です。

---

# HE60 (Original Project)

Below is the original README from the HE60 project, which this keyboard is based on.

---

# HE60

HE60 is a 60% Hall-effect keyboard PCB with 8kHz polling rate, a split spacebar and Tsangan layout support.

## Features

- Support for GH60 tray mount cases e.g., KBDfans Tofu60 Redux, and KBDfans Holy60.
- Support for gummy O-ring mount cases **if the USB-C port is not soldered** e.g., Bakeneko60, and SingaKBD Unikorn (required 10mm JST cable).
- [libhmk](https://github.com/peppapighs/libhmk) firmware.
- [hmkconf](https://hmk.prasertsuk.com) web-based configurator.

## Disclaimer

- The PCB requires standoffs to be mounted to the switch plate. The mounting points are **not compatible** with other available plates e.g., GEON Venom60 7U plate. HE60 v1 plate **is not compatible** with this PCB.

## Supported Layouts

![Layouts](/doc/layout.png)

## Fabrication

The following files are required:

- BOM (Bill of Materials): Contains the list of components required to build the PCB.
- Pick and Place: Contains the placement of the components on the PCB.
- Gerber: Contains the PCB design files for fabrication.

Note that the components in the BOM are all mounted on the bottom side of the PCB, and are based on the available components in JLCPCB at the time of writing. You may need to adjust the components based on your preference or availability. For the JST connector (labeled `JST_SH`), I used `WAFER-SH1.0-4PWB` offered by JLCPCB. **Make sure to deselect the USB-C port when choosing the components to solder if you are using the gummy O-ring version.**

You may change the Hall-effect sensors during the component selection based on your preference, and availability. Different sensors require different calibration values, which can be adjusted using the web-based configurator. Here are some options that I have used:

- GH39FKSW (Cheapest)
- MT9102ET
- SS39ET
- DRV5055A3
- OH49E-S (Discontinued)

The fabrication files above are available [here](https://github.com/peppapighs/HE60/releases).

## Build Guide

The following items are required to build the PCB:

- PCB
- Switch plate (DXF file available [here](/plate.dxf). You may need to use less flexible materials such as aluminum or FR4 to prevent the switch at the top right corner from popping out if you use the alternative backspace layout. If you would like to manufacture FR4 plate along with the PCB, you can find the GERBER file for the plate [here](https://github.com/peppapighs/HE60/releases).)
- Magnetic switches (e.g., GEON Raw HE, Gateron Magnetic Jade, Duhuk Core HE, etc.)
- Stabilizers (**Clip-in stabilizers are required for the gummy O-ring version**)
- M2 3.5mm standoffs x8
- M2 3mm flat head screws x16

1. Install the stabilizers to the PCB.

![Stabilizers](/doc/1-stabilizers.jpg)

2. Attach the standoffs to the PCB using the M2 screws.

![Standoff](/doc/2-standoffs.jpg)

3. Install the switches to the plate. Assemble the plate and PCB together. Press the PCB against the plate to make sure the switches are seated properly. Screw the standoffs to the plate using the rest of the M2 screws.

![Assembled](/doc/3-assembled.jpg)

4. Install the PCB into the case.

![Case with keycaps](/doc/4-complete.jpg/)

## Firmware

Head to [libhmk](https://github.com/peppapighs/libhmk/releases) for a pre-compiled firmware. The firmware can be flashed using DFU mode, which can be entered by holding the BOOT button before plugging in. You may need to install the DFU bootloader driver using Zadig. See [libhmk](https://github.com/peppapighs/libhmk) for more information for firmware flashing instructions.

## Acknowledgements

- Xelus from AEBoards for reviewing the PCB design and providing feedback.
- Keyboard Atelier community for supporting the project.
