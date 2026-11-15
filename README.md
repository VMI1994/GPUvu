# GPUvu

A real-time GPU monitoring application for Linux (NVIDIA) and macOS (Apple Silicon) built with Python and PyQt6.

![Linux GPUvu](./images/linux-gpuvu.png "Linux GPUvu Screenshot")
![macOS GPUvu](./images/mac-gpuvu.png "macOS GPUvu Screenshot")

## Features

- **Real-time GPU Metrics** - 1-second refresh rate
- **Visual GPU usage indicator**
- **VRAM Monitoring** - Real-time memory usage with progress bar
- **Clock Speeds** - GPU, SM, and memory clock monitoring
- **Temperature & Power** - Thermal and power consumption tracking
- **Dark Theme** - Clean, modern dark interface (#1e1e1e)

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

```
$>git clone https://github.com/VMI1994/GPUvu.git
$>cd GPUvu
$>chmod +x 
e binary
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

## Architecture

### Backend
- **Linux**: `NVIDIAGPUManager` using `nvidia-smi`
- **macOS**: `MacGPUManager` using `apple-smi`

### Frontend
- PyQt6 with dark theme (#1e1e1e background, #252526 panels)
- 3x3 grid layout (400x400 window)
- Custom widgets for each metric

## License

MIT License - See LICENSE file for details

## Credits

- Built with PyQt6
- macOS backend: [apple-smi](https://github.com/AppleSMI/apple-smi)
- Linux backend: nvidia-smi

## Contributing
