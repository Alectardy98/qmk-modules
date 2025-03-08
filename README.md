# @getreuer's QMK community modules

(This is not an officially supported Google product.)

| Module                                    | Description                                           |
|-------------------------------------------|-------------------------------------------------------|
| [Achordion](./achordion/)                 | Customize the tap-hold decision.                      |
| [Custom Shift Keys](./custom_shift_keys/) | Customize what keycode is produced when shifted.      |
| [Keycode String](./keycode_string/)       | Format QMK keycodes as human-readable strings.        |
| [Mouse Turbo Click](./mouse_turbo_click/) | Click the mouse rapidly.                              |
| [PaletteFx](./palettefx/)                 | Palette-based animated RGB matrix lighting effects.   |
| [Select Word](./select_word/)             | Convenient word and line selection.                   |
| [Sentence Case](./sentence_case/)         | Automatically capitalize sentences.                   |

TODO: More to come...


## What is this?

This repo contains my community modules for [Quantum Mechanical Keyboard
(QMK)](https://docs.qmk.fm) firmware, used on custom keyboards like the ZSA
Voyager pictured below. I use most of these modules myself in [my QMK
keymap](https://github.com/getreuer/qmk-keymap).

![ZSA Voyager](doc/voyager.jpg)


## License

This repo uses the Apache License 2.0 except where otherwise indicated. See the
[LICENSE file](LICENSE.txt) for details.


## How to install

This repo makes use of the [Community
Modules](https://docs.qmk.fm/features/community_modules) support added in QMK
Firmware 0.28.0, released on 2025-02-27. [Update your QMK set
up](https://docs.qmk.fm/newbs_git_using_your_master_branch#updating-your-master-branch)
to get the latest. If you have it, there will be a `modules` folder inside your
`qmk_firmware` folder.

**Step 1. Download the modules.** Run these shell commands to download the
modules, replacing `/path/to/qmk_firmware` with the path of your
"`qmk_firmware`" folder:

```sh
cd /path/to/qmk_firmware
mkdir -p modules
git submodule add https://github.com/getreuer/qmk-modules.git modules/getreuer
git submodule update --init --recursive
```

Or if using [External
Userspace](https://docs.qmk.fm/newbs_external_userspace), replace the first
line with `cd /path/to/your/external/userspace`.

Or if you don't want to use git, [download a .zip of this
repo](https://github.com/getreuer/qmk-modules/archive/refs/heads/main.zip) into
the `modules` folder. Unzip it, then rename the resulting `qmk-modules-main`
folder to `getreuer`.

By any of the above, the installed directory structure is like this:

    <QMK_FIRMWARE or QMK_USERSPACE>
    └── modules
        └── getreuer
            ├── achordion
            ├── custom_shift_keys
            ├── keycode_string
            └── ...

**Step 2. Add modules to keymap.json.** Add a module to your keymap by writing a
file `keymap.json` in your keymap folder with the content

```json
{
 "modules": ["getreuer/achordion"]
}
```

Or add multiple modules like:

```json
{
 "modules": ["getreuer/achordion", "getreuer/sentence_case"]
}
```

Follow the module's documentation for any further specific set up.

**Step 3. Update the firmware.** Compile and flash the firmware as usual. If
there are build errors, try running `qmk clean` and compiling again for a clean
build.


## How to uninstall

Remove the modules from `keymap.json` and delete the `modules/getreuer` folder.

