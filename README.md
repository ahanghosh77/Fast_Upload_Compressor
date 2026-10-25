# YT Fast Upload Compressor

**By Ahan Ghosh**

A lightweight drag-and-drop tool for Windows that compresses your videos before uploading to YouTube — cutting upload time by 3x to 5x without any visible quality loss.

If you've ever sat around waiting 30-40 minutes for a video to upload on a slow connection, this tool fixes that.

---

## What It Does

- Takes your exported video (MP4, MKV, MOV, AVI — whatever you've got)
- Compresses it using CRF 18 (visually lossless — your viewers won't notice any difference)
- Produces a new `_fast_upload.mp4` file that's **60-75% smaller**
- Your original file stays completely untouched

### Why This Works

Most video editors export at 30-50 Mbps bitrate. YouTube re-encodes everything to ~8-10 Mbps anyway. So you're basically waiting ages to upload data that YouTube throws away immediately.

This tool brings your file down to the sweet spot *before* upload, so you're not wasting time sending unnecessary data.

---

## Requirements

- **Windows 10 / 11**
- **FFmpeg** installed on your system

### Installing FFmpeg

Open PowerShell or Command Prompt and run:

```
winget install Gyan.FFmpeg
```

Restart your terminal after installing. That's it.

---

## How to Use

1. Download `YT_Fast_Upload_Compressor.exe` from the [Releases](../../releases) page
2. Put it anywhere you want (Desktop works great)
3. **Drag and drop** any video file onto the icon
4. Wait for the compression to finish
5. Upload the new `yourfile_fast_upload.mp4` to YouTube Studio

You can also run it from the command line:

```
YT_Fast_Upload_Compressor.exe "C:\path\to\your\video.mp4"
```

---

## Before vs After (Real Example)

| | Before | After |
|---|---|---|
| File Size | 2,006 MB | ~420 MB |
| Bitrate | 25 Mbps | ~5 Mbps |
| Resolution | 2560x1440 | 2560x1440 (unchanged) |
| Quality on YouTube | 1080p/1440p VP9 | 1080p/1440p VP9 (identical) |
| Upload Time (10 Mbps) | ~27 minutes | ~6 minutes |

---

## FAQ

**Will my video look worse?**
No. CRF 18 is the industry standard for "visually lossless" compression. The human eye cannot distinguish the difference. And since YouTube re-compresses everything anyway, both files end up looking identical on the platform.

**Does it delete my original file?**
Never. It creates a brand new file with `_fast_upload` added to the name. Your original is never touched.

**What video formats does it support?**
Anything FFmpeg can read — MP4, MKV, MOV, AVI, WEBM, FLV, WMV, and more.

**Can I use this for videos other than YouTube?**
Yeah, works great for any platform — Instagram, Twitter, Discord, Google Drive, anywhere you need a smaller file.

---

## Technical Details

The compression uses the following FFmpeg pipeline:

- **Codec:** H.264 (libx264), High Profile, Level 4.2
- **Quality:** CRF 18 (visually lossless)
- **Preset:** medium (good balance of speed and compression)
- **Pixel Format:** yuv420p (maximum compatibility)
- **Fast Start:** enabled (YouTube can start processing immediately)
- **Audio:** AAC-LC, 192 kbps, 48 kHz, stereo

---

## License

This tool is free to use for personal purposes. Do not redistribute or resell.

**© 2026 Ahan Ghosh. All rights reserved.**
