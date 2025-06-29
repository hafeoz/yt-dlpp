# YT-DLPP

A tiny yt-dlp wrapper script that optimizes downloads from bilibili and netease
platforms with enhanced danmaku support and intelligent retry mechanisms.

> This script is intended for my personal use and may not be suitable for
> everyone. Use it at your own risk.

## Installation

Download the script to your local bin directory:

```bash
curl -o ~/.local/bin/yt-dlpp https://raw.githubusercontent.com/hafeoz/yt-dlpp/main/yt-dlpp
chmod +x ~/.local/bin/yt-dlpp
```

Make sure `~/.local/bin` is in your PATH, or add it to your shell configuration:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### Dependencies

Following dependencies are required for the script to function properly:

- `yt-dlp` - Core download functionality
- `ffmpeg` - Video/audio processing
- `mkvmerge` (from mkvtoolnix) - Video container manipulation
- `jq` - JSON processing
- `DanmakuFactory` - Danmaku conversion
- `yutto` - Alternative danmaku downloader (optional)

## Usage

### Basic Download

```bash
# yt-dlpp URL [PATH]
yt-dlpp https://www.bilibili.com/video/BV1234567890
```

### Audio Only

```bash
# yt-dlpp -a URL
yt-dlpp --audio https://music.163.com/song/123456
```

### Re-download Existing Video

```bash
# yt-dlpp -v PATH_TO_VIDEO_FILE
yt-dlpp --update-video ./video.mkv
```

### Refresh Danmaku

```bash
# yt-dlpp -u PATH_TO_VIDEO_FILE
yt-dlpp --update-danmaku ./video.mkv
```

### Environment Variables

Configure the script behavior using environment variables:

```bash
# Cookie file for authenticated downloads
export YT_DLP_COOKIE="~/.local/share/youtube-dl/cookies.txt"

# Additional yt-dlp arguments
export YT_DLP_ARGS="--proxy http://proxy:8080"

# Use aria2c as external downloader
export USE_ARIA2="yes"
export ARIA2_ARGS="-x 8 -s 8"

# Custom audio encoding parameters
export AUDIO_ENCODING_PARAMS="-b:a 192k -compression_level 8"

# Disable yutto for danmaku downloading
export USE_YUTTO="no"

# Custom retry settings
export BACKOFF="2s"
```

## License

This software is licensed under
[BSD Zero Clause](https://spdx.org/licenses/0BSD.html) OR
[CC0 v1.0 Universal](https://spdx.org/licenses/CC0-1.0.html) OR
[WTFPL Version 2](https://spdx.org/licenses/WTFPL.html).
You may choose any of them at your will.
