newtab.cmd
==========

newtab.cmd calls the CUI-application in the other tab of WindowsTerminal

```newtab.cmd
@echo off
setlocal
if "%1" == "" (
    echo %0: - Start application in the other tab of WindowsTerminal
    echo Usage: %0 COMMANDNAME
    exit /b 0
)
if "%CURRENTDIRECTORY%" == "" (
    for /F %%I in ('cd') do set "CURRENTDIRECTORY=%%I"
    for /F %%I in ('where %1') do @"%LOCALAPPDATA%\Microsoft\WindowsApps\wt.exe" --window 0 new-tab -- %~dpnx0 %%I %2 %3 %4 %5 %6 %7 %8 %9
) else (
    cd "%CURRENTDIRECTORY%"
    %1 %2 %3 %4 %5 %6 %7 %8 %9
)
endlocal
exit /b 0
```
