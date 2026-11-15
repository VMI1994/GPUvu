# GPUvu
A simple GPU monitor for Linux or Mac Silicon written in Python.

# GPUvu

A real-time GPU monitoring application for Linux (NVIDIA) and macOS (Apple Silicon) built with Python and PyQt6.

![Linux GPUvu](./images/linux-gpuvu.png "Linux GPUvu Screenshot")
![macOS GPUvu](./images/mac-gpuvu.png "macOS GPUvu Screenshot")

## Features

- **Real-time GPU Metrics** - 1-second refresh rate
- **Circular Utilization Gauge** - Visual GPU usage indicator
- **VRAM Monitoring** - Real-time memory usage with progress bar
- **Clock Speeds** - GPU, SM, and memory clock monitoring
- **Temperature & Power** - Thermal and power consumption tracking
- **Dark Theme** - Clean, modern dark interface (#1e1e1e)
- **3x3 Grid Layout** - Compact, space-efficient design (400x400)

## Screenshots

### Linux Version

![Linux GPUvu](./images/linux-gpuvu.png "Linux GPUvu Screenshot")

**Features:**
- NVIDIA GPU monitoring with `nvidia-smi`
- CUDA utilization, temperature, and power usage
- Fan speeds and compute status
- Dark theme with real-time updates

### macOS Version

![macOS GPUvu](./images/mac-gpuvu.png "macOS GPUvu Screenshot")

**Features:**
- Apple Silicon GPU monitoring with `apple-smi`
- Metal GPU utilization and temperature
- Power consumption tracking
- No fan speeds (Apple Silicon has no fans)

## Installation

### Linux (NVIDIA)

```bash
# Install dependencies
pip install PyQt6 pyinstaller nvidia-ml-py

# Run the application
python3 gpu_monitor.py

# Or build the binary
pyinstaller --clean GPUvu.spec
./dist/GPUvu
```

### macOS (Apple Silicon)

```bash
# Install dependencies
pip install PyQt6 pyinstaller apple-smi Pillow

# Run the application
python3 MacGPUvu.py

# Or build the binary
pyinstaller --clean GPUvu.spec
./dist/MacGPUvu
```

## Requirements

### Linux
- Python 3.8+
- NVIDIA GPU with driver
- PyQt6
- nvidia-ml-py

### macOS
- Python 3.8+
- Apple Silicon (M1, M2, M3, etc.)
- PyQt6
- apple-smi
- Pillow

## Project Structure

```
GPUvu/
├── src/
│   ├── gui/
│   │   ├── main_window.py      # Main application window
│   │   └── widgets/            # GUI widgets
│   └── gpu_monitor/
│       ├── mac_gpu.py          # macOS GPU backend
│       └── nvidia.py           # Linux GPU backend
├── GPUvu.spec                   # PyInstaller spec file
├── MacGPUvu.icns                # macOS application icon
├── convert_icon.sh              # Icon conversion script
└── README.md
```

## Architecture

### Backend
- **Linux**: `NVIDIAGPUManager` using `nvidia-ml-py`
- **macOS**: `MacGPUManager` using `apple-smi`

### Frontend
- PyQt6 with dark theme (#1e1e1e background, #252526 panels)
- 3x3 grid layout (400x400 window)
- Custom widgets for each metric

### Metrics Displayed

| Widget | Linux | macOS |
|--------|-------|-------|
| System & Processes | Driver, CUDA, PCI, Processes | N/A |
| VRAM | Used / Total, Percentage | Used / Total, Percentage |
| Clocks | Graphics, SM, Memory, Max | Utilization, Active |
| Temp/Power | Fan, Temp, Power | Temp, Power |
| Gauge | Utilization % | Utilization % |

## Building

### Build Linux Binary

```bash
cd ~/Desktop/GPUvu
source venv/bin/activate
pyinstaller --clean -F -n GPUvu -i icon.png GPUvu.spec
```

### Build macOS Binary

```bash
cd ~/Desktop/GPUvu
source venv/bin/activate
pyinstaller --clean -F -n MacGPUvu -i MacGPUvu.icns GPUvu.spec
```

## Configuration

### Thresholds

Color thresholds for VRAM utilization:
- **Green**: 0-50%
- **Yellow**: 50-80%
- **Orange**: 80-90%
- **Red**: 90-100%

## Troubleshooting

### macOS: "No such file or directory: apple-smi"

The app now uses `apple_smi` Python module directly instead of the external binary. No PATH configuration needed.

### Linux: "No such file or directory: nvidia-smi"

Ensure NVIDIA drivers are installed and `nvidia-smi` is available in your PATH.

## License

MIT License - See LICENSE file for details

## Credits

- Built with PyQt6
- macOS backend: [apple-smi](https://github.com/AppleSMI/apple-smi)
- Linux backend: nvidia-ml-py

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test both Linux and macOS versions
5. Submit a pull request

## Support

For issues or feature requests, please create an issue in this repository.

---

*GPUvu - Real-time GPU monitoring for Linux and macOS*
