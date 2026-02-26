# CH341 Kernel Module

## Description
This package provides a pre-compiled Linux kernel module (`ch341.ko`) sourced from the mainline Linux kernel. It’s offered as a convenience binary for systems where this in-tree module is not included or enabled by default.

### What the Module Does
The `ch341` module is a driver for CH341-based USB-to-serial adapters, commonly found in low-cost USB-to-UART devices. It enables communication between a Linux system and serial peripherals (e.g., microcontrollers, old hardware) via USB, exposing them as `/dev/ttyUSB*` devices.

## Requirements
- **Kernel Version**: Compiled for `5.15.148-tegra` (check your kernel with `uname -r` to confirm compatibility).
- **Root Access**: Required for installation (e.g., via `sudo`).
- **Target System**: Compatible with Linux systems running the specified kernel, such as NVIDIA Tegra-based devices.

## Files
- `ch341.ko`: The pre-compiled kernel module.
- `install_module_ch341.ko.sh`: Script to install and load the module.
- `LICENSE`: Licensing terms (GPL v2).

## Installation
1. **Download**:  
   Get `ch341_module-1.0.tar.gz` and `ch341_module-1.0.tar.gz.sha256`.
2. **Verify Integrity**:  
   Ensure the file is intact:  
   ```bash
   sha256sum -c ch341_module-1.0.tar.gz.sha256
   ```
3. **Extract**:  
   Unpack the tarball:  
   ```bash
   tar -xzf ch341_module-1.0.tar.gz
   ```
4. **Navigate**:  
   Move into the directory:  
   ```bash
   cd ch341_module
   ```
5. **Run the Install Script**:  
   ```bash
   ./install_module_ch341.ko.sh
   ```  
   *Note*: If you see "permission denied," make it executable (rarely needed):  
   ```bash
   chmod +x install_module_ch341.ko.sh
   ```

## Verification
Check if the module is loaded:  
```bash
lsmod | grep ch341
```  
If `ch341` appears, it’s active. Plug in a CH341 device and check `dmesg` or `ls /dev/ttyUSB*` to confirm it’s detected.

## Notes
- **Kernel Compatibility**: Built for `5.15.148-tegra`. It won’t work on other kernel versions without recompilation.
- **In-Tree Status**: The `ch341` module is part of the mainline Linux kernel. This binary is for convenience on systems missing it.
- **Troubleshooting**:  
  - If `modprobe` fails, check `dmesg` for errors (e.g., version mismatch).  
  - Remove any existing `ch341` module if needed:  
    ```bash
    sudo rmmod ch341
    ```

## License
Distributed under the GNU General Public License v2 (see `LICENSE`), per Linux kernel requirements.

## Contact
For issues or requests (e.g., other kernel versions), https://github.com/jetsonhacks/jetson-orin-kernel-builder.
