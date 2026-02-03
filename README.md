# Alacritty Terminal Setup Guide

## Prerequisites

1. **Install JetBrainsMono Nerd Font**
   - Download from: https://www.nerdfonts.com/font-downloads
   - Install the font on Windows
   - Restart any open terminals

2. **Install Starship Prompt**
   ```powershell
   winget install --id Starship.Starship
   ```

## Installation Steps

### 1. Configure Alacritty

Place the `alacritty.toml` file at:
```
C:\Users\divin\AppData\Roaming\alacritty\alacritty.toml
```

**Key Features:**
- Starting directory: `C:\Dev`
- Font: JetBrainsMonoNL Nerd Font
- Kanagawa Wave theme
- 95% opacity with blur
- PowerShell as default shell

### 2. Configure Starship Prompt

1. Create the config directory if it doesn't exist:
   ```powershell
   New-Item -ItemType Directory -Force -Path "$HOME\.config"
   ```

2. Place the `starship.toml` file at:
   ```
   C:\Users\divin\.config\starship.toml
   ```

3. Add Starship to your PowerShell profile:
   ```powershell
   notepad $PROFILE
   ```

4. Add this line to the file:
   ```powershell
   Invoke-Expression (&starship init powershell)
   ```

5. Save and restart your terminal

### 3. Install Kanagawa Theme for Alacritty

The theme is already imported in the config. Make sure you have the theme file at:
```
C:\Users\divin\AppData\Roaming\alacritty\themes\themes\kanagawa_wave.toml
```

If you don't have it, you can:
1. Clone the themes repo: https://github.com/alacritty/alacritty-theme
2. Or download kanagawa_wave.toml directly and place it in the themes folder

## Customization

### Change Starting Directory
Edit `alacritty.toml` and modify the startup command:
```toml
[terminal.shell]
program = "powershell"
args = ["-NoLogo", "-NoExit", "-Command", "Set-Location C:\\YourPath"]
```

### Change Font Size
Edit `alacritty.toml`:
```toml
[font]
size = 11.0  # Change this value
```

### Change Opacity
Edit `alacritty.toml`:
```toml
[window]
opacity = 0.95  # 0.0 (transparent) to 1.0 (opaque)
```

## Starship Prompt Features

- **Language Detection**: Shows icons for Python 🐍, Rust 🦀, Node.js, Java, Go, C/C++
- **Git Integration**: Displays branch name and status
- **Minimal Design**: Two-line prompt with Kanagawa colors
- **Version Display**: Shows language version when in a project directory

## Keyboard Shortcuts (Alacritty)

- `Ctrl + Shift + C` - Copy
- `Ctrl + Shift + V` - Paste
- `Ctrl + +` - Increase font size
- `Ctrl + -` - Decrease font size
- `Ctrl + 0` - Reset font size
- `Ctrl + Shift + N` - New window

## Troubleshooting

### Icons not showing
- Make sure JetBrainsMonoNL Nerd Font is installed
- Restart Alacritty after installing fonts
- Check that the font name is exactly: `JetBrainsMonoNL Nerd Font`

### Starship not working
- Make sure Starship is in your PATH
- Verify PowerShell profile has the init line
- Run `starship --version` to confirm installation

### Theme not loading
- Check that the theme file path is correct
- Ensure all backslashes are properly escaped (`\\`)
- Check the Alacritty log file for errors

### Terminal crashes on startup
- Make sure `C:\Dev` directory exists
- Check that PowerShell is installed
- Review the Alacritty log at: `C:\Users\divin\AppData\Local\Temp\Alacritty-*.log`
