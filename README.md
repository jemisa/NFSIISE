NFSIISE
=======

Need For Speed II SE - Linux port with 3D acceleration and TCP protocol! The game also can run under Windows.

## Compile:

* To compile the game you must have a 32-bit:
 * GCC (or Clang) compiler,
 * YASM assembler,
 * OpenGL devel,
 * SDL2 devel.
* Edit the "compile_nfs" script, modify what do you want. Compile the game by executing the script - it will automaticly generate executable file inside "Need For Speed II SE" directory:
 * `./compile_nfs` - compilation for Linux,
 * `./compile_nfs win32` - cross compilation for Windows.

## Run:

* Copy "fedata" and "gamedata" directories from the Need For Speed II SE original CD-ROM (or from CD image from the Internet) into "Need For Speed II SE" directory.
* You can delete unnecessary files, e.g. "fedata/pc/text/text.*", because TCP version uses new files in root directory.
* All files and directories copied from CD-ROM must have *small letters* on Linux!!!
* If you want to change the language, edit "install.win" file and change the first line. Leave "4nn" as is and modify only language name. Possible languages are:
 * english,
 * french,
 * german,
 * italian,
 * spanish,
 * swedish.
* Run the game.
* The game settings files are located in "~/.nfs2se" ("%AppData%\\.nfs2se" on Windows). At the first run the "nfs2se.conf.template" will be copied there. You can modify the file if you want to configure the game. On Windows you can use "open_config.bat" to open the config file in notepad.
* The game will crash without original game data.

## What works:

* Game controllers (reconnected game controllers should be the same),
* Force Feedback (tested on Linux),
* TCP and UDP connection,
* Serial port connection,
* Brightness,
* Sound.

## What does not work:

* Modem connection (it will never work again, this feature was removed from assembly code),
* Force Feedback might not work on Windows due to bugs in SDL2. You can try to enable it in "nfs2se.conf" file (WindowsForceFeedbackDevice).

## Patches:

* This directory contains patch for SDL 2.0.3 (SDL 2.0.4 has already this bugfix). It allows to use all axes in DualShock3 gamepad! You must also modify "nfs2se.conf" file (Joystick0Axes, Joystick0Buttons).

## Additional information:

* The game doesn't work on OS X due to:
	* window and event loop aren't in main thread - this doesn't work in Cocoa - the game runs, but it can't get any mouse, keyboard and WM events,
	* different stack alignment (OS X needs 16 bytes, the game has 4 bytes) - this is very easy to fix.
* The game is not tested under *BSD systems. Probably it can run after a few code changes.
