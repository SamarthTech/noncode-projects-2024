# FFmpeg Documentation for Windows

## Table of Contents
1. [Introduction](#1-introduction)
2. [Installation](#2--installation)  
    2.1.  [Downloading FFmpeg](#21-downloading-ffmpeg)  
    2.2.  [Setting Environmemt Variables](#22-setting-environment-variables)  
3. [Basic Usage](#3-basic-usage)  
    3.1. [Verifying Installation](#31-verifying-installation)  
    3.2. [Basic Commands](#32-basic-commands)  
4. [FFmpeg Features](#4-ffmpeg-features)  
    4.1. [Converting Video Formats](#41-converting-video-formats)  
    4.2. [Audio Extraction](#42-audio-extraction)  
    4.3. [Video Compression](#43-video-compression)  
    4.4. [Audio Compression](#44-audio-compression)  
    4.5. [Merging Audio and Video Files](#45-merging-audio-and-video-files)  
    4.6. [Splitting and Trimming Video](#46-splitting-and-trimming-video)  
5. [Advanced Usage](#5-advanced-usage)  
    5.1. [Batch Processing](#51-batch-processing)  
    5.2. [Working with Filters](#52-working-with-filters)  
        5.2.1. [Scale Video](#521-scale-video)
        5.2.2. [Add Watermark](#522-add-watermark)
6. [Useful FFmpeg Commands](#6-useful-ffmpeg-commands)  
        6.1. [Convert to GIF](#61-convert-to-gif)  
        6.2. [Change Video Speed](#62-change-video-speed)  
        6.3. [Concatenate Videos](#63-concatenate-videos)  
        6.4. [Add Subtitles](#64-add-subtitles)
7. [Common Errors and Fixes](#7-common-errors-and-fixes)  
        7.1. [Error: Unrecognized option 'foo'](#71-error-unrecognized-option-foo)  
        7.2. [Error: Invalid codec](#72-error-invalid-codec)  
        7.3. [Slow conversion](#73-slow-conversion)  

## 1. Introduction

**FFmpeg** is a powerful, open-source tool for handling video, audio, and other multimedia files and streams. It supports various formats and codecs and provides a command-line interface to encode, decode, transcode, mux, demux, stream, filter, and play almost anything that humans and machines have created. FFmpeg is especially popular for batch processing media files and automating media-related workflows.

This documentation focuses on **installing**, **configuring**, and **using FFmpeg on Windows systems**.  

## 2.  Installation
### 2.1. Downloading FFmpeg
- Official Builds: 
    - Download the latest FFmpeg build from ->  [FFmpeg Official Builds](https://ffmpeg.org/download.html)
    - Choose the correct architecture (64-bit or 32-bit) based on your Windows system.
- Extracting:  
    - Extract the downloaded zip file to a location on your system, e.g., `C:\ffmpeg`.

### 2.2. Setting Environment Variables
To use FFmpeg commands from anywhere in the command line, set the environment variables:

- Right-click on `This PC` > `Properties` > `Advanced system settings`.
- Click on the `Environment Variables` button.
- Under the `System Variables` section, find `Path` and click `Edit`.
- Add the path to the bin directory of FFmpeg (e.g., `C:\ffmpeg\bin`) to the list.
- Click `OK` and restart your terminal.

##  3. Basic Usage
###  3.1. Verifying Installation
After setting the environment variable, verify FFmpeg installation by running:  
```bash
ffmpeg -version
```

This command should display FFmpeg version details and available codecs.  
### 3.2. Basic Commands
- Check input file details:  
```bash
ffmpeg -i inputfile.mp4
```  

This provides detailed information about the input file such as format, codec, resolution, and bitrate.  
- Convert video to another format:  
```bash
ffmpeg -i inputfile.mp4 outputfile.avi
```
## 4. FFmpeg Features  
### 4.1. Converting Video Formats  
To convert video from one format to another, simply specify the input file and the desired output format:  
```bash
ffmpeg -i inputfile.mp4 outputfile.avi
```

FFmpeg automatically detects the file format based on the extension.  

### 4.2. Audio Extraction
You can extract audio from a video file by specifying an audio-only format like MP3 or WAV:  
```bash
ffmpeg -i inputfile.mp4 -q:a 0 -map a outputfile.mp3
```

This extracts the best quality audio available in the file.

### 4.3. Video Compression
To reduce the size of a video while maintaining good quality, use the following command:  
```bash
ffmpeg -i inputfile.mp4 -vcodec libx265 -crf 28 outputfile_compressed.mp4
```

Here, `-crf` (Constant Rate Factor) controls video quality, where a lower number means better quality. Values typically range between 18-28.  

### 4.4. Audio Compression  
To compress audio without affecting video, use:  
```bash
ffmpeg -i inputfile.mp4 -b:a 128k outputfile_compressed.mp4
```

This sets the audio bitrate to `128k`, reducing file size.  

### 4.5. Merging Audio and Video Files  
You can merge an audio file and a video file into a single output:  
```bash
ffmpeg -i video.mp4 -i audio.mp3 -c:v copy -c:a aac outputfile.mp4
```

This keeps the video codec intact and compresses the audio to AAC format.  

### 4.6. Splitting and Trimming Video  
To split a video from a specific start time and duration:  
```bash
ffmpeg -i inputfile.mp4 -ss 00:01:00 -t 00:00:30 -c copy outputfile.mp4
```

Here, `-ss` specifies the start time, and `-t` is the duration.  

##  5. Advanced Usage  
### 5.1. Batch Processing  

To convert multiple files in a folder, create a batch script (`.bat` file):  
```bash
for %%a in (*.mp4) do ffmpeg -i "%%a" "outputfolder\%%~na.avi"
```

This script converts all `.mp4` files in the current folder to `.avi` format and places the output in the `outputfolder`.  

### 5.2. Working with Filters  
FFmpeg allows you to apply various filters to manipulate videos:  

### 5.2.1. Scale Video:  
```bash
ffmpeg -i inputfile.mp4 -vf scale=1280:720 outputfile.mp4
```

### 5.2.2. Add Watermark:  
```bash
ffmpeg -i inputfile.mp4 -i watermark.png -filter_complex "overlay=10:10" outputfile.mp4
```

## 6. Useful FFmpeg Commands  
### 6.1. Convert to GIF:  
```bash
ffmpeg -i inputfile.mp4 -vf "fps=10,scale=320:-1" outputfile.gif
```

### 6.2. Change Video Speed:  
```bash
ffmpeg -i inputfile.mp4 -filter:v "setpts=0.5*PTS" outputfile.mp4
```

### 6.3. Concatenate Videos:  
```bash
ffmpeg -f concat -safe 0 -i filelist.txt -c copy outputfile.mp4
```
`filelist.txt` should contain:
```bash
file 'part1.mp4'
file 'part2.mp4'
```

### 6.4. Add Subtitles:  
```bash
ffmpeg -i inputfile.mp4 -vf subtitles=subtitlefile.srt outputfile.mp4
```

## 7. Common Errors and Fixes  
### 7.1. Error: `Unrecognized option 'foo'`:  
- This happens when the command has a typo or uses an unsupported feature. Double-check your syntax.

### 7.2. Error: `Invalid codec`:  
Ensure the codec specified is supported. You can list supported codecs by running:  
```bash
ffmpeg -codecs
```

### 7.3. Slow conversion:  
If FFmpeg runs slow, consider changing the number of threads with:  
```bash
ffmpeg -i inputfile.mp4 -threads 4 outputfile.mp4
```

---

This documentation provides an overview of FFmpeg’s core functionality on Windows. For more advanced features, refer to the official [FFmpeg documentation](https://ffmpeg.org/documentation.html).

---
