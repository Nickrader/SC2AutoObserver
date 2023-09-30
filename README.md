# Sc2AutoObserver

## Known Issues:
Seems to be having problems (crashing) with replays from prior 'versions' of Starcraft II client.
9/29/2023

## About
Starcraft 2 replays auto observer inspired by the [SSCAIT-ObserverModule](https://github.com/Plankton555/SSCAIT-ObserverModule).  
The Sc2AutoObserver is used to view replays on the [SC2 AI Arena 24/7 livestream](https://www.twitch.tv/aiarenastream)

## Build requirements
1. Download (the password is iagreetotheeula) at least one of the following map packs:
  * [Ladder 2019 Season 3](http://blzdistsc2-a.akamaihd.net/MapPacks/Ladder2019Season3.zip)

2. Put the downloaded maps into the Maps folder (create it if the folder doesn't exist):
  * Windows: C:\Program Files\StarCraft II\Maps
  * OS X: /Applications/StarCraft II/Maps

3. Download and install [CMake >= 3.10](https://cmake.org/download/).

4. A compiler with C++17 support.

5. Install [Google test >= 1.10.0](https://github.com/google/googletest)

5. Windows: Download and install [Visual Studio](https://www.visualstudio.com/downloads/)

6. OS X: Install XCode.

## Build instructions

### Windows (Visual Studio)
```bat
:: Clone the project.
$ git clone --recursive git@github.com:Nickrader/SC2AutoObserver.git
$ cd sc2autoobserver

:: Create build directory.
$ mkdir build
$ cd build

:: Create Visual Studio project files.
:: For Visual Studio 2022.
$ cmake ../ -G "Visual Studio 17 2022"
:: For Visual Studio 2019.
$ cmake ../ -G "Visual Studio 16 2019"
:: For Visual Studio 2017.
$ cmake ../ -G "Visual Studio 15 2017 Win64"

:: Build the project using Visual Studio.
$ start Observer.sln

:: Launch the observer. (based upon what you built in Visual Studio)
:: e.g. bin\Debug\Observer.exe --Path "C:\Users\CoolUsername\Documents\StarCraft II\Accounts\84555555\1-S2-1-5555555\Replays\Multiplayer\Alcyone LE.SC2Replay" --Speed "0.25x"
:: Release version
$ bin\Release\Observer.exe --Path "<Path to a single SC2 replay or directory with replay files>" --Speed <Replay speed>`
:: Debug version
$ bin\Debug\Observer.exe --Path "<Path to a single SC2 replay or directory with replay files>" --Speed <Replay speed>`
```

### OS X (Xcode)
```bash
# Clone the project.
$ git clone --recursive git@gitlab.com:aiarena/sc2autoobserver.git && cd sc2autoobserve

# Create build directory.
$ mkdir build && cd build

# Generate a Makefile.
# Use 'cmake -DCMAKE_BUILD_TYPE=Debug ../' if debuginfo is needed
# Debug build also contains additional debug features and chat commands support.
$ cmake ../ -G Xcode

# Build the project using Xcode.
$ open Observer.xcodeproj/

# Launch the observer.
$ ./bin/Observer --Path "<Path to a single SC2 replay or directory with replay files>" --Speed <Replay speed>`
```

## Load replays from an older SC2 versions
To load replays from older an older SC2 version, one should additionally specify game version hash and path to the older SC2 executable, e.g. for 4.10 version:
### Windows
```bat
$ bin/Observer.exe --Path "C:\Users\lladdy\Documents\358809_TyrZ_DoogieHowitzer_IceandChromeLE.SC2Replay" -- -d "B89B5D6FA7CBF6452E721311BFBC6CB2" -e "D:\Battle.net\StarCraft II\Versions\Base75689\SC2.exe"
```
### OS X
```bash
$ ./bin/Observer --Path "/Users/alkurbatov/Downloads/358809_TyrZ_DoogieHowitzer_IceandChromeLE.SC2Replay" -- -d "B89B5D6FA7CBF6452E721311BFBC6CB2" -e "/Applications/StarCraft II/Versions/Base75689/SC2.app/Contents/MacOS/SC2"
```

## License
Copyright (c) 2017 Daniel K�hntopp

Licensed under the [MIT license](LICENSE).
