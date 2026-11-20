# wallpicker

A full-screen wallpaper carousel for macOS. It opens on the wallpaper that is set now, shows the previous and next pictures on either side with their filenames, and sets the chosen picture as the wallpaper on every display and Space.

Part of [monochrome-macos-rice](https://github.com/orioshavfx/macos-monochrome-rice). It also works on its own.

## Build

Needs macOS 13 or newer and the Swift toolchain (Xcode or the Command Line Tools).

```sh
git clone https://github.com/orioshavfx/wallpicker
cd wallpicker
swift build -c release
mkdir -p ~/bin && cp "$(swift build -c release --show-bin-path)/wallpicker" ~/bin/
```

## Use

Run `wallpicker` from a terminal, or bind it to a key (the rice binds it to Opt+W).

| Key | Action |
| --- | --- |
| ← / → | Move to the previous or next picture |
| Return, Enter or Space | Set the highlighted picture as the wallpaper and close |
| Escape or Q | Close without changing anything |

## Settings

Create `~/.config/wallpicker/config.toml`:

```toml
folder = "~/Pictures/Wallpapers"
accent = "#ffffff"
```

- `folder` is where the pictures come from. The default is `~/Pictures/Wallpapers`, which is created if it does not exist.
- `accent` is the colour of the carousel labels and highlight, as a hex value.

## How the wallpaper is set

wallpicker writes the wallpaper store that macOS reads, `~/Library/Application Support/com.apple.wallpaper/Store/Index.plist`, and restarts `WallpaperAgent`. Before the first change, the original store is copied to `~/.local/state/monochrome-macos-rice/wallpaper-backup`.

If macOS refuses the write, allow `wallpicker` under System Settings > Privacy & Security > Full Disk Access.

## Licence

MIT, see [LICENSE](LICENSE).
