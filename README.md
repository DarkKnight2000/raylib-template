# Simple Raylib template in C

## Features:

- Includes raylib. No need to install anything. Makes it easy to update raylib without breaking other projects

- Obj files are created in a separate folder to keep the working tree clean
- Incremental building. Build only compilation units that are changed
- Separate build directories based on version and platform
- Automatically copy all assets (in res/ folder) to build directory along with the app. Makes it easier to ship your game
- Tested on Windows for Desktop and Android platforms. Uses Makefiles from raylib repo with some modifications, so it should work for other platforms also
- Includes a Makefile.Reset file which recompiles raylib to required platform and starts building the project. Useful when switching and testing between different platforms


## Setup


    git clone https://github.com/DarkKnight2000/raylib-c-template.git
    cd raylib-c-template
    mkdir obj
    mkdir build
    mkdir external
    cd external
    git clone https://github.com/raysan5/raylib --depth 1

- Look at [Directory Structure](#directory-structure) for more info about folders


## Usage

- All these commands should be run in the project root
- When building for first time or switching platforms. This rebuilds raylib to required platform and builds the project
```
# for Desktop
make -f Makefile.Reset desktop

# for Android
make -f Makefile.Reset android
```

- For Android, look at Makefile.Android file and set `JAVA_HOME`, `ANDROID_HOME`, `ANDROID_NDK` paths correctly. The Makefile.Android is taken from `raylib` repo so look at [Raylib Wiki](https://github.com/raysan5/raylib/wiki/Working-for-Android) for details.

- For subsequent builds

```
make
```

## Directory Structure:

- .vscode/
  - Containes some useful settings when working with Visual Studio Code
- build/
  - All the build files are created here ready for shipping along with assets
- external/
  - Containes raylib. Pull latest changes and rebuild (you can use Makefile.Reset) for latest changes
- include/
  - Folder for your project header files here
- res/
  - Folder for your assets
  - Copied on each build to the build directory
  - Use the path "res/{asset-name}" in the code to reference the assets
- src/
  - Folder for C source files
