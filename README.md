[![exDesktop: put a star on GitHub](docs/banner.png)](https://github.com/qvkap/exDesktop-linux/stargazers)

<img src="docs/logo.png" width="150" align="left"/>

## exDesktop
*[Licensed under the GNU General Public License v3.0](LICENSE)*

An unofficial Linux client built from the official [Telegram Desktop](https://github.com/telegramdesktop/tdesktop) sources. It adds a customizable settings suite, channel feed, streamer tools and a native Python plugin engine.

[![Channel](https://img.shields.io/badge/Channel-Telegram-blue.svg)](https://t.me/exDesktop)
[![GitHub](https://img.shields.io/badge/GitHub-qvkap%2FexDesktop--linux-blue.svg)](https://github.com/qvkap/exDesktop-linux)
[![Developer](https://img.shields.io/badge/Developer-@qvkap-blue.svg)](https://t.me/qvkap)

![exDesktop settings](docs/screenshots/main.png)

## Features
- Settings for General, Appearance, Chats, Navigation, Plugins and Other.
- Native Linux support with full Wayland and X11 integration.
- Material Design 3 controls, adjustable avatar corners and custom themes.
- Channel feed, wide posts, precise timestamps, edit marks and forward counts.
- Streamer mode with per chat settings, exceptions and screen capture protection.
- Python plugin engine powered by system Python 3 C API (with per plugin settings and automatic safe mode).
- Gemini chat with your own API key.
- User IDs, data center and estimated registration date in profiles.

![Plugin manager](docs/screenshots/plugins.png)

## Downloads
Get the Linux binary and packages from the [releases page](https://github.com/qvkap/exDesktop-linux/releases). The Python plugin runtime is installed into `/usr/share/exDesktop/python/extera/` or detected locally.

## API credentials
Get your own API ID and hash from [Telegram's API credentials page](https://core.telegram.org/api/obtaining_api_id). Pass them to CMake when generating project files:

```bash
-DTDESKTOP_API_ID=YOUR_API_ID -DTDESKTOP_API_HASH=YOUR_API_HASH
```

## Build on Linux

### Dependencies
- **CMake** >= 3.16 & C++20 compiler (GCC >= 12 or Clang >= 15)
- **Qt6** (Core, Gui, Widgets, Network, OpenGL, DBus, Wayland, Svg, ImageFormats)
- **Python 3** Development headers (`python3-dev` / `dev-lang/python`) 3.11 – 3.14
- Standard Telegram Desktop libraries: `tg_owt`, `ffmpeg`, `openal`, `opus`, `rnnoise`, `libjpeg-turbo`, `xxhash`, `minizip`, `ada`, `cld3`, `wallet-engine-telegram`

### Building via CMake
```bash
cmake -B build -G Ninja \
    -DCMAKE_BUILD_TYPE=Release \
    -DQT_VERSION_MAJOR=6 \
    -DDESKTOP_APP_DISABLE_QT_PLUGINS=ON \
    -DTDESKTOP_API_ID="YOUR_API_ID" \
    -DTDESKTOP_API_HASH="YOUR_API_HASH"

cmake --build build --target Telegram
```

### Building on Gentoo / Portage
An ebuild `net-im/exdesktop` is available:
```bash
emerge net-im/exdesktop
```

### Python Plugin Runtime Setup
Copy the Python host runtime files to `/usr/share/exDesktop/python/extera/`:
```bash
sudo mkdir -p /usr/share/exDesktop/python/extera
sudo cp -r Telegram/SourceFiles/extera/python/* /usr/share/exDesktop/python/extera/
```

## Localization
Most strings follow Telegram Desktop translations. exDesktop specific strings are available in English and Russian.

## Thanks
- [Telegram Desktop](https://github.com/telegramdesktop/tdesktop)
- [AyuGram Desktop](https://github.com/AyuGram/AyuGramDesktop)

