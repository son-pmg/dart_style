This is a fork of the [dart_style](https://github.com/dart-lang/dart_style) package modified to support Allman indentation style. This file is not part of the original dart_style package. I added it to provide a build and setup guide for using my forked version of the dart_style package with Visual Studio Code (VS Code).

The changes made in this version of the dart_style package are as follows:

- 4-space indentation instead of 2-space indentation.
- Allman indentation style places opening brackets ({) on a new line, aligned with the left margin. Both opening and closing brackets ({ and }) are aligned in the same column.

# Building the dart_style package

Change directory to your cloned dart_style package:

```sh
cd <path_to_your_dart_style>/dart_style
```

(Optional) Disable analytics:
```sh
dart --disable-analytics
```

Install dependencies:
```sh
dart pub get
```

---

## Windows

### Build

```powershell
dart compile exe bin/format.dart -o bin/dart_style.exe
```

### Setup Visual Studio Code

1. Install [Custom Local Formatters](https://github.com/JKillian/vscode-custom-local-formatters) extension from the VS Code Marketplace by jkillian 

2. Edit C:\Users\\**\<username\>**\AppData\Roaming\Code\User\settings.json

```
    "dart.enableSdkFormatter": false,
    "customLocalFormatters.formatters": [
        {
            "command": "<path_to_your_dart_style>/dart_style/bin/dart_style.exe --output=show --summary=none --page-width=220 ${file}",
            "languages": ["dart"]
        }
    ],
    "[dart]": {
        "editor.defaultFormatter": "jkillian.custom-local-formatters",
        "editor.formatOnSave": false,
    },
```
Where
  - **\<username\>** is your Windows username.
  - **\<path_to_your_dart_style\>** is the path to your cloned dart_style  package.

### dart_style.exe command options

  - --output=show
    - Displays the reformatted code directly in the Dart file after formatting. If you approve of the changes, you can manually save the file.
    - **Do not remove this option!**
  - --summary=none
    - Hides the summary of changes; otherwise, an unwanted summary text will be added at the bottom of the reformatted Dart file.
    - **Do not remove this option!**
  - --page-width=220
    - This is optional.
    - Set the maximum line width to 220 characters. It is best to set it no shorter than **120** characters for better readability of your code.
    - Default is 80.

### To format Dart files in VS Code

Open the Dart file you want to format, and press **Alt + Shift + F** to invoke the dart_style.exe command. If there are changes, press **Ctrl + S** to save them.