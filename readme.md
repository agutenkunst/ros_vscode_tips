# VSCode Tips for ROS Development

This document shares some tips and recommendations for using VSCode for ROS development.

## Extensions - Overview

### General
- [Visual Studio Code Extension for ROS](https://marketplace.visualstudio.com/items?itemName=ms-iot.vscode-ros) [(Details)](#vscode-ros-extension---details)
  - Automatically configures various paths
  - Enables clang-format
- [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)


### C/C++
- [C/C++ for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
  - For Intellisense/Autocompletion

### Python
- ToDo

### Misc
- [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
  - Checkout/Review/Create PRs from within VSCode

- [Trailing Spaces](https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces)
  - Removes/highlights trailing spaces

- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

## VSCode ROS Extension - Details

### C++ Autocompletion
In order to have C++ Autocompletion via Intellisense [C/C++ for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) is needed.

During the first startup in a new workspace a file `.vscode/c_cpp_properties.json` is created at the root of the workspace. This files contains the paths intellisense indexes. **To make sure everythink is properly configured the workspace should be sourced before the first start of vscode.** A proper `.vscode/c_cpp_properties.json` looks something like:

    {
      "configurations": [
        {
          "browse": {
            "databaseFilename": "",
            "limitSymbolsToIncludedHeaders": true
          },
          "includePath": [
            "/opt/ros/foxy/include/**",
            "/home/alex/ros2_ws/src/my_package/include/**",
            "/usr/include/**"
          ],
          "name": "ROS"
        }
      ],
      "version": 4
    }

After the first start of vscode the intellisense is building its index. Depending on the hardware resources and the 
number of files the may take a few seconds. The process is visualized by a small database icon at the lower right.
TODO include image.

If all these settings are applied correctly autocomplete for C++ should now work as expected and show suggestions
during typing. Use <kbd>Strg</kbd>+<kbd>Space</kbd> to show the documentation for each suggestion.


### Clang-Format
 - Directly enables clang-format according to ROS style (see https://github.com/ms-iot/vscode-ros/blob/1a31e7eab9b159fd785c21dd0c1edb2d859814b9/src/cpp-formatter.ts#L10-L56)
   - Needs clang-format installed. (sudo apt-get install clang-format)
   - Usage: (Strg+Shift+P) "Format Document" or "Format Document with ... ROS"

## VSCode GitLense Extension - Details
- Right click: Copy Remote Url

## Sources
- https://github.com/RoboGnome/VS_Code_ROS