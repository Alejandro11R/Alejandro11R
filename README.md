<div align="center">

```
 ██████╗ ███████╗████████╗██████╗  ██████╗
 ██╔══██╗██╔════╝╚══██╔══╝██╔══██╗██╔═══██╗
 ██████╔╝█████╗     ██║   ██████╔╝██║   ██║
 ██╔══██╗██╔══╝     ██║   ██╔══██╗██║   ██║
 ██║  ██║███████╗   ██║   ██║  ██║╚██████╔╝
 ╚═╝  ╚═╝╚══════╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝
```

### play music with command line 🎵

> play music, then keep working on the terminal.

![Release](https://img.shields.io/github/v/release/XORbit01/retro?style=for-the-badge&logo=github&logoColor=cba6f7&labelColor=1e1e2e&color=313244)
![License](https://img.shields.io/github/license/XORbit01/retro?style=for-the-badge&logoColor=a6e3a1&labelColor=1e1e2e&color=313244)
![Issues](https://img.shields.io/github/issues/XORbit01/retro?style=for-the-badge&logoColor=f38ba8&labelColor=1e1e2e&color=313244)
![Stars](https://img.shields.io/github/stars/XORbit01/retro?style=for-the-badge&logoColor=f9e2af&labelColor=1e1e2e&color=313244)
![Forks](https://img.shields.io/github/forks/XORbit01/retro?style=for-the-badge&logoColor=89b4fa&labelColor=1e1e2e&color=313244)
![Watchers](https://img.shields.io/github/watchers/XORbit01/retro?style=for-the-badge&logoColor=89dceb&labelColor=1e1e2e&color=313244)

</div>

---

## 🗺️ Map

- [📦 Installation](#-installation)
- [🎮 Music management](#-music-management)
- [🎧 Playlist management](#-playlist-management)
- [🚦 Controls](#-controls)
- [⚙️ Configuration](#️-configuration)
- [💾 Cache](#-cache)
- [🌐 Update](#-update)
- [📝 License](#-license)
- [📢 Acknowledgments](#-acknowledgments)

---

## 📦 Installation

**Install Retro**

```bash
wget https://github.com/XORbit01/retro/releases/download/v0.0.46/installer.tar.gz
tar -xvf installer.tar.gz
chmod +x installer.sh
./installer.sh
```

> This installer is for Linux systemd-based systems. On other systems, install manually by compiling from source and running the server with `make build`.

**Uninstall Retro**

```bash
~/.local/bin/uninstall_retro.sh
```

---

## 🎮 Music management

**Play music**

```bash
retro play "Despacito - Luis Fonsi"                       # search and play music by name
retro play "https://www.youtube.com/watch?v=kJQP7kiw5Fk"  # play music by url
retro play queue_music                                    # play music from queue (by index too)
retro play ~/Music/Despacito.mp3                          # play music by file path
retro play ~/Music/                                       # play every song in a directory
retro play playlist_name                                  # play music from a playlist
```

> The `play` command is smart enough to detect the source: name, url, file path, directory path, queue, or playlist. Music already in queue is prioritized.

**Status**

```bash
retro status  # 🎵 check queue status: downloading | searching, playing | paused, songs in queue
```

**Pause / Resume**

```bash
retro pause   # ⏸️
retro resume  # ▶️
```

**Next / Previous**

```bash
retro next  # ⏭️
retro prev  # ⏮️
```

**Remove music from queue**

```bash
retro remove music_name  # 🗑️ remove by name
retro remove 1           # 🗑️ remove by index
```

**Adjust volume**

```bash
retro vol 50  # 🎚️ set volume to 50%
retro vol 0   # 🔇 mute
```

**Stop queue**

```bash
retro stop  # 🛑
```

---

## 🎧 Playlist management

**Create playlist**

```bash
retro list create my_playlist  # 📂
```

**Add music to playlist**

```bash
retro list add my_playlist "Despacito - Luis Fonsi"                       # ➕ search and add
retro list add my_playlist "https://www.youtube.com/watch?v=kJQP7kiw5Fk"  # ➕ add by url
retro list add my_playlist queue_music                                    # ➕ add from queue
```

> You can also add by file path or queue index/name.

**Remove music from playlist**

```bash
retro list remove my_playlist "Despacito - Luis Fonsi"  # ➖ remove by name
retro list remove my_playlist 1                          # ➖ remove by index
```

**Show playlist**

```bash
retro list my_playlist  # 📂 show all songs in the playlist
```

**Play playlist**

```bash
retro list play my_playlist  # 📂 queue up every song in the playlist
```

**Delete playlist**

```bash
retro list remove my_playlist  # 📂 delete the whole playlist
```

---

## 🚦 Controls

**Logs**

```bash
retro logs        # 📜 last 200 lines
retro logs info   # 📢 info logs only
retro logs error  # 🚫 error logs only
retro logs warn   # ⚠️ warning logs only
```

**Theme**

```bash
retro theme pink    # 🧼
retro theme purple  # 🔮
retro theme blue    # 🌊
# TODO: retro theme custom
```

**Help**

```bash
retro help       # ❓ show all commands
retro help play  # ❗ show help for the play command
```

---

## 💾 Cache

```bash
retro cache        # 💾 show all cached data
retro cache clear  # 🧹 clear all cache
```

---

## ⚙️ Configuration

**Config file**

The config file lives by default at `~/.retro/config.json`. If it doesn't exist yet:

```bash
mkdir -p ~/.retro
touch ~/.retro/config.json
```

**Default config**

```json
{
  "retro_path": "~/.retro/",
  "path_ytldpl": "yt-dlp",
  "path_ffmpeg": "ffmpeg",
  "path_ffprobe": "ffprobe",
  "search_timeout": 60000000000,
  "theme": "pink",
  "db_path": "~/.retro/retro.db",
  "discord_rpc": false,
  "log_file": "~/.retro/retro.log",
  "server_port": "3131"
}
```

> 📝 You can edit the config manually — it's straightforward.

**Notes**

- ☝️ After changing the config file, restart the service: `systemctl --user restart retro`
- ⚠️ The config file overrides default values.
- 🤖 Set up the autocompletion script for a smoother experience — see `retro completion`.

---

## 🌐 Update

```bash
retro update  # updates retro to the latest version on GitHub
```

---

## 📝 License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for details.

---

## 📢 Acknowledgments

<div align="center">

```
  retro is made with ❤️
```

![](https://img.shields.io/badge/made%20with-catppuccin%20mocha-1e1e2e?style=flat-square&logoColor=cba6f7)

</div>
