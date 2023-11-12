# Windows Terminal

## Supported Commands

- **cd**: Literally, change directory
- **ls**: List the items in the working directory
- **echo**: Spit out the argument list, default to command line
- **doskey**: Alias a name to a command until the terminal window closes

## Common Tasks

**Writing a new file**: `echo " " > [FILE_NAME]`

## Batch Files

You can easily write batch files that will work on the windows terminal. My experience with this is a handful of batch files, usually for navigation, like toSWEP.bat:
``` Batch
@echo off

doskey returnToRoot=cd /D C:/Users/wjpla
doskey openNPP=start Notepad++.exe

if "%1"=="" echo -------------------------------
if "%1"=="" echo - Where would you like to go? -
if "%1"=="" echo -------------------------------

set lib[1].name=wpPersWiki
set lib[1].path=C:/Users/wjpla/Documents/wiki
if "%1"=="%lib[1].name%" cd /D %lib[1].path% 
if "%1"=="" echo -- %lib[1].name%: %lib[1].path%

set lib[0].name=homeServer
set lib[0].path=D:/Documents/Home/Code/homeServer
if "%1"=="%lib[0].name%" cd /D %lib[0].path% 
if "%1"=="" echo -- %lib[0].name%: %lib[0].path%
```

Note: While `%1` refers to the first command line argument, you can reference variables that you `set` by referencing them as `%NAME%`