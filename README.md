# Build Image Linux Kernel For Lichee Pi Nano

This project contains scripts and build outputs for compiling a Linux kernel for the **Lichee Pi Nano (Allwinner F1C100s)** board.

It is based on a legacy Sunxi kernel source.

---

## 📌 Overview

- Platform: Lichee Pi Nano (Allwinner F1C100s)
- Architecture: ARM (arm-linux-gnueabi)
- Kernel Source: https://github.com/robot9706/lichee-pi-nano-linux
- Toolchain: Linaro GCC 6.3.1 (2017.05)
- Host OS: Kali Linux

---

## 🖼️ Board Image

![Lichee Pi Nano](https://github.com/user-attachments/assets/5e4a0026-2524-4e19-be50-aad61e341c40)

---

## ⚙️ Requirements

Install dependencies:

```bash
sudo apt update
sudo apt install -y \
build-essential \
bc \
bison \
flex \
libssl-dev \
libncurses-dev \
libelf-dev \
git \
wget
````
# P2 Connection wifi over MicroSD
````
Phần_cứng_sử_dụng

Board:_Lichee_Pi_Nano

SoC:_Allwinner_F1C100s

RAM:_32MB

Flash:_SPI_NOR_16MB

Wi-Fi:_ESP8089_SDIO

Giao_tiếp_debug:_UART_qua_CP2102,_baudrate_115200
<img width="778" height="468" alt="image" src="https://github.com/user-attachments/assets/b8f13340-0344-4bc8-b3c8-59a3214945f9" />


Sipeed_Lichee_Nano_With16M_Flash_Linux_Version_IOT_Internet_of_Things

Bố_cục_SPI_NOR

mtd0:_00070000_"uboot"_448_KiB

mtd1:_00010000_"dtb"_64_KiB

mtd2:_00480000_"kernel"_4.5_MiB

mtd3:_00b00000_"rootfs"_11_MiB

Tổng:_0x01000000_=_16_MiB

Kết_quả_boot

Kernel_đã_mount_rootfs_trực_tiếp_từ_SPI_NOR:
<img width="822" height="723" alt="image" src="https://github.com/user-attachments/assets/b386f490-840e-4af0-b272-e90ccf4cfd60" />


VFS:_Mounted_root_(squashfs_filesystem)_readonly_on_device_31:3.

Run_/linuxrc_as_init_process

Kết_quả_bộ_nhớ_RAM:
<img width="853" height="103" alt="image" src="https://github.com/user-attachments/assets/ba21c2c6-76c0-4ac6-b976-fe9e236a6214" />


Mem:_total_23728_KB,_used_5140_KB,_available_16144_KB

Swap:_0

Driver_chip_esp8089:
<img width="390" height="61" alt="image" src="https://github.com/user-attachments/assets/00f3eb95-a18d-4b64-a737-9c05087297ed" />


WLAN
<img width="856" height="177" alt="image" src="https://github.com/user-attachments/assets/4883138b-e063-42e6-aed1-760b1551a18f" />
<img width="859" height="67" alt="image" src="https://github.com/user-attachments/assets/5d59252f-611a-43f8-add6-28b98a6780ee" />

SCAN_Wifi
<img width="863" height="141" alt="image" src="https://github.com/user-attachments/assets/1addf5e7-faa1-4aab-8d55-91a51fa2018d" />

Connect_wifi:
<img width="636" height="618" alt="image" src="https://github.com/user-attachments/assets/caf10f43-cf90-41e6-a9a8-11fba982bd8a" />


killall_wpa_supplicant

rm_-rf_/var/run/wpa_supplicant

mkdir_-p_/var/run/wpa_supplicant

cat_>_/tmp/wpa.conf_<<'EOF'

ctrl_interface=/var/run/wpa_supplicant

network={

____ssid="FPT_Telecom_Wifi_7_2.4Ghz"

____psk="12345678"

}

EOF

wpa_supplicant_-B_-Dnl80211,wext_-iwlan0_-c/tmp/wpa.conf

sleep_8

wpa_cli_-p_/var/run/wpa_supplicant_-i_wlan0_status
