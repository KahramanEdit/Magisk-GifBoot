<div align="center">

# 🎬 GifBoot (Boot Animation Maker)
### Turn any GIF or Video into a Custom Android Boot Animation.

[![Magisk](https://img.shields.io/badge/Magisk-Module-blueviolet?style=for-the-badge&logo=android)](https://github.com/topjohnwu/Magisk)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-green?style=for-the-badge)](https://kernelsu.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)

A Magisk/KernelSU module script that converts your favorite GIFs or videos into a perfectly scaled Android `bootanimation.zip` tailored to your device's exact screen resolution.

</div>

---

## 📖 The Problem
Creating a custom boot animation manually is a headache. You have to extract video frames, resize them to match your phone's resolution, create a `desc.txt` file with the correct formatting, and zip it without compression. If the resolution or frame rate is off, the animation lags or doesn't play at all.

## 💡 The Solution
**GifBoot** automates the entire process. It uses `ffmpeg` to extract and perfectly scale the frames to your device's screen size, generates the required `desc.txt`, packages it into an uncompressed `bootanimation.zip`, and places it inside the Magisk module path. On your next reboot, Magisk mounts it seamlessly over the system's default boot animation.

## ✨ Features
- **Auto-Resolution:** Automatically detects your device's screen resolution.
- **Intelligent Scaling:** Crops and scales the video to fit perfectly.
- **No-Compression Zip:** Creates the required uncompressed format.
- **Magisk Overlay:** Places the file safely in the system path.
- **Termux Integration:** Auto-detects `ffmpeg` and `zip` binaries.

## ⚠️ Important Limits (Max FPS)
- **Max 17 FPS:** Android's boot sequence has strict timeout limits. Using higher frame rates (like 30 or 60 FPS) will result in extreme lag or the animation freezing. It is highly recommended to keep it between **10 and 15 FPS**.
- **Storage Space:** Converting a long video into hundreds of high-res PNGs takes up significant space in `/data/local/tmp` during processing.

## 📱 Requirements
- **Root** (Magisk / KernelSU)
- **ffmpeg** (Install via Termux: `pkg install ffmpeg`)
- **zip** (Install via Termux: `pkg install zip`)
- Terminal emulator or WebUI.

## 🚀 Usage (CLI)
If you are running the script manually via Termux as root:

```bash
su
cd /data/adb/modules/gifboot
sh convert.sh /sdcard/Download/video.mp4 12
```

(Replace video.mp4 with your file path and 12 with your FPS).

Once the script says "TAMAM" (OK), simply reboot your device!

📁 Folder Structure

```text
Magisk-GifBoot/
├── META-INF/
│   └── com/google/android/
│       ├── update-binary
│       └── updater-script
├── module.prop
├── convert.sh
└── webroot/
```

⚠️ Disclaimer

· Use at your own risk.
· Modifying system files can lead to bootloops. Always ensure you know how to boot into Safe Mode.
· The developer is not responsible for any damage to your device.

👨‍💻 Author

you

· Feel free to open an issue if you encounter any bugs!

---

<div align="center">
If this module gave your phone a cool new look, give the repo a ⭐!
</div>
