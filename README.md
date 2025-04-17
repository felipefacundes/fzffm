# FZF File Manager

![FZF File Manager Demo](FZFFM.gif)

A powerful, feature-rich terminal file manager built with `bash` and `fzf`, inspired by `ranger` and `lesspipe`. This manager provides intuitive navigation, file operations, and previews with extensive customization options.

## 🌟 Features

- **Intuitive Navigation**:
  - Keyboard-driven interface with Vim-like keybindings
  - Directory browsing with `exa`/`ls` fallback
  - Hidden file toggle and recursive search

- **Rich File Previews**:
  - Adjustable preview pane width (20-150 via `Ctrl-h`/`Ctrl-l`)
  - Syntax highlighting for text files (`bat`/`highlight`/fallbacks)
  - Image thumbnails (`magick`/`viu`/`chafa`)
  - PDF text extraction (`pdftotext`)
  - Archive contents listing
  - Media file information

- **Comprehensive File Operations**:
  - Copy, move, delete files/directories
  - Create symlinks
  - Mark multiple files for batch operations
  - Create files/directories
  - Extract archives to folders
  - Copy file contents to clipboard

- **Advanced Functionality**:
  - Persistent settings in `~/.cache`
  - ANSI colors/icons support
  - Debug logging system
  - Temporary file cleanup
  - Configurable keybindings

## 📦 Installation

### Dependencies

Core requirements:
- `bash` (v4.4+)
- `fzf` (fuzzy finder)
- Core utilities (`ls`, `find`, `file`, etc.)

Recommended for full functionality:
- Preview tools: `bat`, `highlight`, `glow`, `pdftotext`
- Image tools: `imagemagick`, `viu`, `chafa`
- Archive tools: `atool`, `bsdtar`, `7z`
- Media tools: `ffmpeg`, `mediainfo`

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/felipefacundes/fzffm.git
   cd fzffm
   ```

2. Make the script executable:
   ```bash
   chmod +x fzffm
   ```

3. (Optional) Create a symlink to your PATH:
   ```bash
   ln -s $(pwd)/fzffm /usr/bin/fzffm
   ```

## 🚀 Usage

Basic invocation:
```bash
./fzffm [starting_directory]
```

### Key Bindings

#### Navigation
| Key          | Action                          |
|--------------|---------------------------------|
| ↑/↓          | Move selection up/down          |
| Tab/Shift-Tab| Move selection up/down          |
| Enter/Right  | Open selected file/directory    |
| Left         | Go up one level                 |
| Ctrl-q       | Exit file manager               |

#### View Modes
| Key    | Action                          |
|--------|---------------------------------|
| Ctrl-p | Toggle preview panel            |
| Ctrl-h | Increase preview margin (+5)    |
| Ctrl-l | Decrease preview margin (-5)    |
| F5     | Refresh current view            |
| Alt-h  | Toggle hidden files             |
| Alt-c  | Toggle cyclic scrolling         |

#### File Operations
| Key    | Action                          |
|--------|---------------------------------|
| Alt-a  | Toggle mark/unmark file         |
| Ctrl-a | Toggle mark all files           |
| Alt-x  | Mark all files in directory     |
| Ctrl-d | Delete selected/marked files    |
| Ctrl-v | Move selected/marked files      |
| Ctrl-y | Copy selected/marked files      |
| Ctrl-s | Create symlink                  |
| Alt-e  | Extract archive to folder       |
| Ctrl-n | Create new directory            |
| Alt-n  | Create new file                 |

## ⚙️ Configuration

Configuration files are stored in:
- `~/.cache/fzffm/` - Persistent settings
- `~/.config/fzffm/fzffm.conf` - Main configuration

### Customizing Keybindings

Edit `~/.config/fzffm/fzffm.conf` to modify keybindings. Example excerpt:

```ini
# Navigation keys
PREVIEW_KEY_CHILD1="ctrl-l"              # Enter directory/open file
PREVIEW_KEY_PARENT1="ctrl-h"             # Go to parent directory
PREVIEW_KEY_SCROLL_DOWN1="down"          # Scroll down
PREVIEW_KEY_SCROLL_UP1="up"              # Scroll up

# File operations
PREVIEW_KEY_COPY="ctrl-y"                # Copy file
PREVIEW_KEY_MOVE="ctrl-v"                # Move file
PREVIEW_KEY_ERASE="ctrl-e"               # Delete file
```

### Preview Settings

Customize preview behavior with these settings:

```ini
# Preview appearance
PREVIEW_MARGIN=50                   # Text wrap margin
RESOLUTION=960x540                  # Image/video preview size

# Tool preferences
PREVIEW_MARKDOWN=1                  # 1:glow, 2:bat, 3:mdless, 4:mdcat, 5:markdown_reader.sh
PREVIEW_IMG=1                       # 1:img2sixel, 2:viu, 3:catimg, 4:chafa
```

## 🛠️ Troubleshooting

### Common Issues

1. **Missing previews**:
   - Install required tools (`bat`, `highlight`, etc.)
   - Check debug logs in `$TMPDIR/fzffm-debug.log`

2. **Performance issues**:
   - Disable image previews for remote sessions
   - Reduce preview margin size

3. **Keybind conflicts**:
   - Customize bindings in config file

### Debugging

Enable verbose logging by checking:
```bash
tail -f ${TMPDIR}/fzffm-debug.log
```

## 📜 License

GPLv3 - See [LICENSE](LICENSE) file for details.

## 🙏 Credits

- **Felipe Facundes** - Original author
- `fzf` - For the powerful fuzzy finding interface
- `ranger`/`lesspipe` - Inspiration for preview system

---

💡 **Tip**: Press `?` or `F1` anytime to view the full help menu with all keybindings!