# Windows Terminal

## Supported Commands

- **cd**: Literally, change directory
- **ls**: List the items in the working directory
- **echo**: Spit out the argument list, default to command line
- **doskey**: Alias a name to a command until the terminal window closes

## Common Tasks

**Writing a new file**: `echo " " > [FILE_NAME]`

## Batch Files

You can easily write batch files that will work on the windows terminal. My experience with this is a handful of batch files, usually for navigation, like nav.bat:

``` Batch
@echo off

set dbg=0

doskey nav="C:/Users/wjpla/nav.bat" $1
doskey openNPP=start Notepad++.exe

if "%1"=="" echo -------------------------------
if "%1"=="" echo - Where would you like to go? -
if "%1"=="" echo -------------------------------
if %dbg%==1 echo DEBUG Argument: %1

call :checkRoute "%1" root C:/Users/wjpla/
call :checkRoute "%1" wpPersWiki C:/Users/wjpla/Documents/wiki
call :checkRoute "%1" homeServer D:/Documents/Home/Code/homeServer
call :checkRoute "%1" article-examination D:/Documents/Home/Code/article-examination
call :checkRoute "%1" csc600 D:/Documents/School/2022/Fall/csc600
call :checkRoute "%1" csc667 D:/Documents/School/2022/Fall/csc667

exit /B %ERRORLEVEL%

:checkRoute
if %dbg%==1 echo DEBUG Dir Name: %~2
if %dbg%==1 echo DEBUG Dir Path: %~3
if %dbg%==1 echo DEBUG Checking that "%~1" is equal to "%~2"
if "%~1"=="%~2" cd /D %~3
if "%~1"=="" echo -- %~2: %~3
exit /B 0
```

Note: While `%1` refers to the first command line argument, you can reference variables that you `set` by referencing them as `%NAME%`. When using functions, you can refer to function arguments as `%~1`, and, when declaring aliases with doskey, use `$1` to refer to the first command line argument.