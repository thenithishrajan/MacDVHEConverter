# DVHEConverter

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/platform-macOS-blue.svg)](https://www.apple.com/macos)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()
[![Code Style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)]()

> Professional-grade MKV to MP4 converter with Dolby Vision HDR support, designed for high-performance media processing pipelines.

## 🚀 Key Features

- **High-Performance Processing**: Optimized for maximum throughput with minimal quality loss
- **Dolby Vision Support**: Full HDR profile preservation (Profile 5)
- **Batch Processing**: Intelligent directory scanning and parallel processing capabilities
- **Real-time Monitoring**: Advanced progress tracking with detailed status reporting
- **Error Recovery**: Robust error handling with automatic recovery mechanisms
- **Resource Management**: Efficient temporary file handling and cleanup
- **Format Preservation**: Maintains original video quality and metadata

## 📋 Requirements

### System Requirements

- **OS**: macOS 10.15 (Catalina) or later
- **CPU**: Intel i5/Apple M1 or higher recommended
- **RAM**: Minimum 8GB, 16GB recommended
- **Storage**: SSD recommended for optimal performance

### Dependencies

- **FFmpeg** (4.4+)
- **mp4demuxer_mac** (latest version)
- **mp4muxer_mac** (latest version)

## 💻 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/dvheconverter.git

# Navigate to directory
cd dvheconverter

# Set execution permissions
chmod +x dvheconverter

# Install dependencies (using Homebrew)
brew install ffmpeg

# Verify installation
./dvheconverter --version
```

## 🔧 Configuration

Create a configuration file at `~/.dvheconverter/config.json` (optional):

```json
{
  "output_directory": "/path/to/default/output",
  "temp_directory": "/path/to/temp",
  "logging_level": "info"
}
```

## 📖 Usage

### Basic Usage

```bash
# Single file conversion
./dvheconverter -i input.mkv

# Directory processing
./dvheconverter --dir /path/to/mkv/files

# Specify output directory
./dvheconverter -i input.mkv --output-dir /custom/output
```

### Advanced Options

```bash
# Custom processing with specific options
./dvheconverter -i input.mkv \
  --output-dir /custom/output \
  --temp-dir /custom/temp
```

### Environment Variables

```bash
# Set default configuration
export DVHE_OUTPUT_DIR="/path/to/output"
export DVHE_TEMP_DIR="/path/to/temp"
export DVHE_LOG_LEVEL="debug"
```

## 🎯 Command Line Interface

| Option             | Description                          | Default  |
| ------------------ | ------------------------------------ | -------- |
| `-i, --input-file` | Input MKV file path                  | -        |
| `--dir`            | Input directory for batch processing | -        |
| `--output-dir`     | Output directory path                | ./output |
| `--temp-dir`       | Temporary processing directory       | ./temp   |

## 🔄 Processing Pipeline

1. **Initialization Phase**

   - Configuration validation
   - Resource allocation
   - Directory structure preparation

2. **Processing Phase**

   - Input validation
   - Stream analysis
   - Format conversion
   - HDR profile preservation

3. **Post-processing Phase**
   - Quality verification
   - Metadata preservation
   - Resource cleanup

## 📊 Status Display Format

```
========================================
DVHEConverter - Processing Status
========================================
Input File    : example.mkv
Progress      : [##########] 100%
Status        : Converting
Time Elapsed  : 00:02:34
Estimated Time: 00:03:45
CPU Usage     : 45%
Memory Usage  : 1.2GB
```

## 📁 Output Structure

```
output/
├── completed/
│   ├── video1_completed.mp4
│   └── video2_completed.mp4
├── logs/
│   ├── conversion.log
│   └── error.log
└── temp/
    └── processing/
```

## 🔍 Error Codes

| Code | Description        | Resolution                                             |
| ---- | ------------------ | ------------------------------------------------------ |
| E001 | Invalid input file | Verify file exists and has correct permissions         |
| E002 | Conversion failed  | Check FFmpeg installation and file integrity           |
| E003 | Insufficient space | Free up disk space or specify alternate temp directory |
| E004 | Demuxer error      | Update mp4demuxer_mac to latest version                |

## 🛠 Troubleshooting

### Common Issues

1. **Conversion Fails with E002**

   ```bash
   # Verify FFmpeg installation
   ffmpeg -version

   # Check file permissions
   chmod 644 input.mkv
   ```

2. **Performance Issues**
   ```bash
   # Optimize for performance
   ./dvheconverter -i input.mkv --temp-dir /fast/ssd/path
   ```

## 📈 Performance Optimization

- Use SSD for temporary directory
- Process files in batches of optimal size
- Monitor system resources during conversion

## 🔒 Security Considerations

- Input validation for all file paths
- Secure temporary file handling
- Resource limits enforcement
- Permission verification

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📮 Support

- Documentation: [Wiki](https://github.com/yourusername/dvheconverter/wiki)
- Issues: [GitHub Issues](https://github.com/yourusername/dvheconverter/issues)
- Discussions: [GitHub Discussions](https://github.com/yourusername/dvheconverter/discussions)

## 🙏 Acknowledgments

- FFmpeg team for the underlying conversion engine
- Dolby Vision team for HDR specifications
- Open source community for various contributions

---

**Note**: This tool is optimized for professional video processing workflows. For issues and feature requests, please refer to our [contribution guidelines](CONTRIBUTING.md).
