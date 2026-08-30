<div align="center">

<img src="https://readme-typing-svg.herokuapp.com/?font=JetBrains+Mono&size=32&pause=1000&color=CBA6F7&center=true&vCenter=true&width=500&height=60&lines=retro" />

**play music with the command line, then keep working**

<br/>

![release](https://img.shields.io/github/v/release/XORbit01/retro?style=for-the-badge&logoColor=cba6f7&labelColor=11111b&color=1e1e2e)
![license](https://img.shields.io/github/license/XORbit01/retro?style=for-the-badge&logoColor=a6e3a1&labelColor=11111b&color=1e1e2e)
![stars](https://img.shields.io/github/stars/XORbit01/retro?style=for-the-badge&logoColor=f9e2af&labelColor=11111b&color=1e1e2e)
![issues](https://img.shields.io/github/issues/XORbit01/retro?style=for-the-badge&logoColor=f38ba8&labelColor=11111b&color=1e1e2e)
![go](https://img.shields.io/badge/built%20with-go-1e1e2e?style=for-the-badge&logo=go&logoColor=89dceb&labelColor=11111b)

<br/>

<img src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif" width="600px"/>

</div>

<br/>

`retro` busca, descarga y reproduce música desde YouTube (o tu disco) directo en la terminal — sin abrir el navegador, sin dejar el shell.

```bash
retro play "Despacito - Luis Fonsi"
```

y listo, sigue sonando mientras trabajas. 🎧

<br/>

## ✨ Por qué retro

| | |
|---|---|
| 🔍 **Busca por lo que sea** | nombre, URL, ruta de archivo, carpeta completa o playlist — `retro` detecta la fuente solo |
| 📼 **Cola inteligente** | prioriza lo que ya pusiste en cola antes de buscar algo nuevo |
| 🎧 **Playlists reales** | crea, edita, reproduce y borra playlists desde la terminal |
| 🎨 **Temas** | pink, purple, blue — o el tuyo propio (en camino) |
| 🌐 **Se auto-actualiza** | `retro update` y ya tienes la última versión desde GitHub |
| 🪶 **Ligero** | un solo binario, systemd service, sin dependencias raras aparte de `yt-dlp` y `ffmpeg` |

<br/>

## 📦 Quick start

```bash
wget https://github.com/XORbit01/retro/releases/download/v0.0.46/installer.tar.gz
tar -xvf installer.tar.gz
chmod +x installer.sh
./installer.sh
```

> Pensado para Linux con systemd. ¿Otro sistema? compílalo desde código fuente con `make build`.

Desinstalar:

```bash
~/.local/bin/uninstall_retro.sh
```

<br/>

## 🚀 Uso básico

```bash
retro play "Despacito - Luis Fonsi"                      # buscar y reproducir por nombre
retro play "https://www.youtube.com/watch?v=kJQP7kiw5Fk" # reproducir por url
retro play ~/Music/                                       # reproducir toda una carpeta
retro status                                               # ver qué está sonando
retro pause / retro resume                                 # pausar / reanudar
retro next / retro prev                                    # siguiente / anterior
retro vol 50                                                # ajustar volumen
```

<br/>

## 📖 Referencia completa

<details>
<summary><b>🎮 Gestión de música</b></summary>
<br/>

```bash
retro play "Despacito - Luis Fonsi"                       # buscar y reproducir por nombre
retro play "https://www.youtube.com/watch?v=kJQP7kiw5Fk"  # reproducir por url
retro play queue_music                                     # reproducir desde la cola (por índice también)
retro play ~/Music/Despacito.mp3                            # reproducir por ruta de archivo
retro play ~/Music/                                          # reproducir todo lo de una carpeta
retro play playlist_name                                    # reproducir una playlist

retro status         # 🎵 ver estado: descargando/buscando, reproduciendo/pausado, cola
retro pause          # ⏸️
retro resume         # ▶️
retro next           # ⏭️
retro prev           # ⏮️
retro remove music_name   # 🗑️ quitar de la cola por nombre
retro remove 1            # 🗑️ quitar de la cola por índice
retro vol 50          # 🎚️ volumen al 50%
retro vol 0           # 🔇 mute
retro stop            # 🛑 detener la cola
```

</details>

<details>
<summary><b>🎧 Gestión de playlists</b></summary>
<br/>

```bash
retro list create my_playlist                                       # 📂 crear playlist

retro list add my_playlist "Despacito - Luis Fonsi"                 # ➕ agregar buscando
retro list add my_playlist "https://www.youtube.com/watch?v=..."    # ➕ agregar por url
retro list add my_playlist queue_music                               # ➕ agregar desde la cola

retro list remove my_playlist "Despacito - Luis Fonsi"               # ➖ quitar por nombre
retro list remove my_playlist 1                                      # ➖ quitar por índice

retro list my_playlist       # 📂 ver canciones de la playlist
retro list play my_playlist  # 📂 encolar toda la playlist
retro list remove my_playlist # 📂 borrar la playlist completa
```

</details>

<details>
<summary><b>🚦 Controles y logs</b></summary>
<br/>

```bash
retro logs         # 📜 últimas 200 líneas
retro logs info    # 📢 solo info
retro logs error   # 🚫 solo errores
retro logs warn    # ⚠️ solo warnings

retro theme pink    # 🧼
retro theme purple  # 🔮
retro theme blue    # 🌊
# TODO: retro theme custom

retro help        # ❓ ver todos los comandos
retro help play   # ❗ ayuda del comando play
```

</details>

<details>
<summary><b>💾 Cache</b></summary>
<br/>

```bash
retro cache        # 💾 ver todo lo cacheado
retro cache clear  # 🧹 limpiar cache
```

</details>

<details>
<summary><b>⚙️ Configuración</b></summary>
<br/>

El archivo vive en `~/.retro/config.json`. Si no existe:

```bash
mkdir -p ~/.retro
touch ~/.retro/config.json
```

Config por defecto:

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

- ☝️ Tras editar el config, reinicia el servicio: `systemctl --user restart retro`
- ⚠️ El config sobreescribe los valores por defecto
- 🤖 Configura el autocompletado con `retro completion` para mejor experiencia

</details>

<details>
<summary><b>🌐 Update</b></summary>
<br/>

```bash
retro update
```

Actualiza retro a la última versión publicada en GitHub.

</details>

<br/>

## 📝 Licencia

MIT — mira [LICENSE](./LICENSE) para más detalles.

## 📢 Agradecimientos

Gracias a nuestro sponsor **@HelloHabiba** ☕

<div align="center">


<img src="https://visitor-badge.laobi.icu/badge?page_id=XORbit01.retro" />

</div>
