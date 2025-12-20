<h1 align="center">Vortex Console boot splash theme</h1>

> This is a fork of the awesome
> [Vortex Ubuntu Plymouth Theme](https://github.com/emanuele-scarsella/vortex-ubuntu-plymouth-theme)
> by [@emanuele-scarsella](https://github.com/emanuele-scarsella).

---

Animated Plymouth theme with a console-style appearance and
a futuristic and elegant look.

The splash image color wheel spins at varying speeds creating a vortex
effect. Simultaneously, the logo spins in the opposite direction.

Disk encryption password prompt is supported.

## Examples

|                                                      |                                                      |
| :--------------------------------------------------: | :--------------------------------------------------: |
|                        Bootup                        |                       Shutdown                       |
|         ![Boot splash animated demo][bootup]         |      ![Shutdown splash animated demo][shutdown]      |
|                       Password                       |                       Question                       |
| ![Boot splash with password animated demo][password] | ![Boot splash with question animated demo][question] |

## ⚙️ Installation

To install the theme and set it as the default, navigate to the
repository directory and invoke the `install` script:

```bash
cd path/to/vortex-console-plymouth-theme
./install
```

`install` invokes `sudo` so you will be asked for your password.

## ✏️ Editing the theme

Feel free to edit the theme to your liking. You could replace images or even edit the script files.
After editing the theme, first [install](#gear-installation) it and then [preview](#paintbrush-preview--testing) it.

## 🖌️ Preview / Testing

To preview the theme make sure you install the `plymouth-x11` package:

```bash
sudo apt install plymouth-x11
```

To preview the currently active Plymouth theme, navigate to the
repository directory and invoke the `test` script:

```bash
cd path/to/vortex-console-plymouth-theme

# Show Plymouth preview for 10 seconds
./test

# Show Plymouth with mock password and question/answer prompts,
# then show splash for 10 more seconds
./test prompt
```

`test` invokes `sudo` so you will be asked for your password.

## 🚫 Removal

To remove the theme, navigate to the repository directory and invoke
the `uninstall` script:

```bash
cd path/to/vortex-console-plymouth-theme
./uninstall
```

`uninstall` invokes `sudo` so you will be asked for your password.

The uninstallation process will prompt you to set a new theme. The
default Plymouth theme in Ubuntu 22.04 is `bgrt`.

## 🔧 Customization

### Console output

By default, the theme now displays boot console messages in a
semi-transparent box at the bottom of the screen. This shows all the
system startup actions in real-time, similar to a traditional text boot.

To disable the console output box, edit
`vortex-console/vortex-console.script` and comment out or remove the
console box initialization section (starting at line 79) and the status
update callback function.

The console box can be customized by adjusting these variables near the
top of the script:

- `console_box_offset_x` - Horizontal offset from screen edges (default: 30)
- `console_box_offset_y` - Vertical offset from screen edges (default: 30)
- `console_box_padding` - Padding inside the box (default: 10)
- `console_max_lines` - Maximum number of lines to display
  (default: calculated based on screen height)
- `console_line_height` - Height of each line in pixels (default: 21)

### Logo spin

To disable the logo image spin, edit
`vortex-console/vortex-console.script` and change `logo_spin = -0.009;`
to `logo_spin = 0;` near the top.

### Background color

To change the background color, edit
`vortex-console/vortex-console.script` and modify the
`Window.SetBackgroundTopColor()` and `Window.SetBackgroundBottomColor()`
values. The parameters are RGB values (0-1 range). For example, to set a
dark blue background:

```javascript
Window.SetBackgroundTopColor(0, 0, 0.2);
Window.SetBackgroundBottomColor(0, 0, 0.2);
```

Additionally, you should comment out the bg lines like this

```javascript
// bg = Sprite(Image("bg.png").Scale(screen.w, screen.h));
// bg.SetZ(0);
```

to rely solely on the script-defined background color.

After modification, reinstall the theme with `./install` as described
above.

### Background image

Replace `vortex-console/bg.png` in the repository with your desired
background image. Your image must be in PNG format. After modification,
reinstall the theme with `./install` as described above.

## 📄 License

This project is licensed under the GNU General Public License (GPL)
version 2. See [`LICENSE`][license] for more information.

## 🙏 Acknowledgments

- Original theme created by
  [@emanuele-scarsella](https://github.com/emanuele-scarsella)

## 🤝 Contributions

- Original repository:
  [vortex-ubuntu-plymouth-theme](https://github.com/emanuele-scarsella/vortex-ubuntu-plymouth-theme)
- Forked and adapted as "Vortex Console" with console-focused
  enhancements
