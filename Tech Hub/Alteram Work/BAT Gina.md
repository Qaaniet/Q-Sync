#hub/tech #category/technition #alteram 
```
@echo off
setlocal EnableExtensions

:: ============================
:: Auto-Admin
:: ============================
whoami /groups | find "S-1-16-12288" >nul 2>&1
if not %errorlevel%==0 (
    :: Not elevated—relaunch via PowerShell RunAs
    powershell -NoProfile -ExecutionPolicy Bypass -Command ^
      "Start-Process -FilePath '%~f0' -Verb RunAs"
    exit /b
)

:: ============================
:: Qaaniet's BAT
:: ============================

:: --- Configuration ---
set "MSI_PATH=C:\temp\Gina_v10.msi"
set "SERVERNAME=sassa.local"
set "PORTNO=443"
set "INSTALLATION_KEY=XzhO8AhAlYWx4oHviq4Vi3VtYKxSfKJa9IUotWZmAEcu1Bq1c68qHnh4wwanZBqq"
set "LOG_PATH=%TEMP%\Gina_v10_install.log"

:: --- Validate MSI file exists ---
if not exist "%MSI_PATH%" (
    echo [ERROR] MSI not found: "%MSI_PATH%"
    exit /b 2
)

echo Starting install: %MSI_PATH%
echo Logging to: %LOG_PATH%"
echo.

:: --- Install with basic UI ---
msiexec.exe /i "%MSI_PATH%" /qb /l*v "%LOG_PATH%" SERVERNAME="%SERVERNAME%" PORTNO="%PORTNO%" INSTALLATION_KEY="%INSTALLATION_KEY%"
set "ERR=%ERRORLEVEL%"

echo.
if %ERR% equ 0 (
    echo [SUCCESS] Installation completed.
) else (
    echo [FAIL] msiexec returned code %ERR%. See log: "%LOG_PATH%"
)

exit /b %ERR%
```

