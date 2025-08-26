# Omarchy Theme Builder

A template-based theme builder for creating consistent desktop themes across multiple applications for Omarchy

## Quick Start

```bash
# Build and install the example theme
./omarchy-theme-build themes/desert-twilight --install

# Create your own theme
mkdir themes/my-theme
cp themes/desert-twilight/colors.sh themes/my-theme/
# Edit themes/my-theme/colors.sh with your colors
# Add background images to themes/my-theme/ 
./omarchy-theme-build themes/my-theme --install

```

## Why?
- For quickly creating a custom color palette that complements your favorite photo or illustration you wish to set as wallpaper.  
- or just as a starting point for further refinement and customization.


## How It Works

### 1. Theme Folders
Each theme lives in its own folder under `themes/` containing:
- `colors.sh` - Color definitions (required)
- Background images (optional) - Any `.jpg`, `.png`, `.webp` files

Example theme included:
- `themes/desert-twilight/` - Warm sandstone theme + Wadi Rum at night background (photo © jg-k)

### 2. Build Script
Generate theme files from a theme folder:

```bash
./omarchy-theme-build themes/desert-twilight       # Build theme
./omarchy-theme-build themes/my-theme --light      # Build with light mode
./omarchy-theme-build themes/my-theme --install    # Build and install to Omarchy
```

**Options:**
- `--light` / `-l`: Creates a `light.mode` file in output
- `--install` / `-i`: Installs theme to `~/.config/omarchy/themes/` and switches to it
- `--help` / `-h`: Shows usage information

### 3. Template Processing
- Templates in `templates/` contain placeholders like `${BG}`, `${FG}`, etc.
- The script uses `envsubst` to replace placeholders with color values
- Output is saved to `output/THEME_NAME/`
- Background images from theme folder are automatically copied

## Usage Workflow

1. **Create a new theme folder:**
   ```bash
   mkdir themes/my-new-theme
   cp themes/desert-twilight/colors.sh themes/my-new-theme/
   # Edit themes/my-new-theme/colors.sh with your colors
   ```

2. **Add background images (optional):**
   ```bash
   cp ~/Pictures/my-wallpaper.jpg themes/my-new-theme/
   ```

3. **Build and install the theme:**
   ```bash
   ./omarchy-theme-build themes/my-new-theme --install
   ```

The `--install` flag will:
- Build the theme
- Copy it to `~/.config/omarchy/themes/`
- Switch to the new theme automatically

## Color Variables Reference

### Core Colors
- `BG` - Main background color
- `FG` - Main foreground/text color

### Terminal Palette
- `BLACK`, `RED`, `GREEN`, `YELLOW` - Standard ANSI colors
- `BLUE`, `MAGENTA`, `CYAN`, `WHITE` - Standard ANSI colors

### UI Elements
- `ACCENT` - Primary accent color (used for highlights, active elements)
- `BORDER_ACTIVE` - Active window/element borders
- `BORDER_INACTIVE` - Inactive window/element borders
- `SELECTION_BG` - Background for selected items
- `CURSOR` - Terminal cursor color

### Icon Theme
- `ICON_THEME` - Yaru icon variant name
  - Options: `Yaru`, `Yaru-blue`, `Yaru-dark`, `Yaru-magenta`, `Yaru-olive`, `Yaru-prussiangreen`, `Yaru-purple`, `Yaru-red`, `Yaru-sage`, `Yaru-wartybrown`, `Yaru-yellow`

## What It Does

Generates unified theme files for:
- **Alacritty** - Terminal emulator colors
- **Btop** - System monitor colors  
- **Hyprland** - Window manager borders
- **Hyprlock** - Screen locker colors
- **Icons** - File manager icon theme
- **Mako** - Notification daemon styling
- **Neovim** - Text editor colors
- **SwayOSD** - On-screen display styling
- **Walker** - Application launcher theme
- **Waybar** - Status bar colors
- **Chromium** - Chromium background color

### Neovim disclaimer
- I don't use vim and am not familiar with neovim extensions...
