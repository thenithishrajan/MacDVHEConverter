# DVHEConverter

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/platform-macOS-blue.svg)](https://www.apple.com/macos)

> A macOS tool for converting MKV files to MP4 format with Dolby Vision HDR support.

## 🚀 Key Features

- **MKV to MP4 Conversion**: Convert MKV files while preserving video quality
- **Dolby Vision Support**: HDR profile preservation (Profile 5)
- **Batch Processing**: Process multiple MKV files from a directory
- **Real-time Status**: Live progress tracking with visual progress bar
- **Resource Management**: Automatic temporary file handling and cleanup

## 📋 Requirements

### Dependencies

- **FFmpeg**
- **mp4demuxer_mac**
- **mp4muxer_mac**

## 💻 Installation

```bash
# Set execution permissions
chmod +x dvheconverter

# Install FFmpeg if not already installed
brew install ffmpeg
```

## 🔧 Configuration

The tool supports an optional configuration file at `./config.json`:

```json
{
  "output_dir": "/path/to/default/output",
  "temp_dir": "/path/to/temp",
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

## 🎯 Command Line Options

| Option             | Description                          | Default  |
| ------------------ | ------------------------------------ | -------- |
| `-h, --help`       | Show help message                    | -        |
| `-i, --input-file` | Input MKV file path                  | -        |
| `--dir`            | Input directory for batch processing | -        |
| `--output-dir`     | Output directory path                | ./output |
| `--temp-dir`       | Temporary processing directory       | ./temp   |

## 🔄 Processing Pipeline

1. **Converting**

   - Converts MKV to temporary MP4 format
   - Uses FFmpeg for initial conversion

2. **Demuxing**

   - Separates audio and video streams
   - Supports AAC/EC3 audio and H264/H265 video

3. **Muxing**
   - Combines streams with Dolby Vision profile
   - Applies DV Profile 5 with DVH1 flag

## 📊 Status Display

```
=========================================
DVHEConverter - DV MKV to MP4 Conversion Tool
=========================================

Total Files : 1
Completed   : 0
Errors      : 0

File Statuses:
--------------
1. example.mkv [Processing]

Progress: [##########] 100%
```

## 📁 Output Structure

```
output/
└── input_directory_name/      # For directory mode
    └── filename_completed.mp4 # Converted files
temp/
└── input_directory_name/      # For directory mode
    └── filename_temp.mp4     # Temporary files
```

## 🔍 Error Handling

The script handles several error scenarios:

- Invalid input file/directory
- FFmpeg conversion failures
- Demuxing/muxing errors
- Missing audio/video streams
- File permission issues

## 🛠 Troubleshooting

Common error messages and solutions:

- "File does not exist" - Verify file path and permissions
- "Failed to convert to MP4" - Check FFmpeg installation
- "Demuxing failed" - Verify mp4demuxer_mac is working
- "Audio or video files not found" - Check input file integrity
- "Muxing failed" - Verify mp4muxer_mac is working

## 📝 License

This project is licensed under the MIT License.

---

**Note**: This tool is designed for converting MKV files to MP4 format while preserving Dolby Vision HDR content.
