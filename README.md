<h1 align="center">
    <img src="./media/logo.png" width="200" height="200" />
    <br>
    SourceCode watchface for Tizen
    <br>
</h1>

This is a simple watchface for Tizen operating system (tested on Samsung Galaxy Watch Active 2 with Tizen 5.5.0.2). Watchface is styled as C# source code with Visual Studio default color scheme. It displays current time, date, battery level and steps count.

## Preview
<p align="center">
    <img src="./media/preview1.png" />
    <br>
    <br>
    <img src="./media/preview2.png" />
</p>

## Installation
Because GalaxyWatchStudio is no longer supported by Samsung, installation is a bit tricky. Very helpful is [this forum post](https://forum.developer.samsung.com/t/getting-samsung-distributor-certificate/27222/82).

Installation steps:
1. On watch enable debugging mode and connect to same Wi-Fi network as your PC. Debugging mode can be enabled in `Settings -> About watch -> Debugging `.
2. <strong>Reboot your watch</strong> (this is important step).
3. Open Galaxy Watch Studio and file from this repository `vscoding.gwd`.
4. Connect to your watch by entering its IP address.
5. Open Tizen Studio and using `Tools -> Package Manager -> Extension SDK` install extensions: `Samsung Certificate Extension` and `Samsung Wearable Extension`.
6. After installation go back to Tizen Studio and in `Tools -> Device Manager -> Remote Device Manager (right second icon)` add your watch (connection On).
7. In Tizen Studio go to `Tools -> Certificate Manager -> +` and create new certificate profile. <strong> Type of certificate is `Samsung`.</strong>
8. Close Tizen Studio and GalaxyWatchStudio and go to `C:\Users\{your_user}\SamsungCertificate\{name_of_certificate_profile}` and copy content of this folder to these (and content in these folder delete before):
   - `C:\Program Files\Galaxy Watch Studio\tizen\keystore`
   - `C:\Users\{your_user}\GearWatchDesigner\keystore`
   - `C:\Fit2Installer\cert`
9. Open GalaxyWatchStudio and `vscode.gwd` file from this repository.
10. Press F10 to build watchface and enter your certificate password.
11. It will display error message after building, but watchface should be built in file `vscoding_TW5.tpk` (same folder where is `vscode.gwd`).
12. Using Fit2Installer install `vscoding_TW5.tpk` on your watch:
    - copy `vscoding_TW5.tpk` to `sign_me` folder in Fit2Installer
    - run `connect.bat` (type your watch IP address and press Enter, it will probably display error message, but when you will run it again it should be already connected)
    - run `sign.bat` (type your certificate password and press Enter)
    - run `install.bat`
    - run `disconnect.bat`
13. Watchface should be installed on your watch. In `Settings -> Apps -> Permissions` allow all permissions for this watchface.
14. Change watchface to `SourceCode` by holding on current watchface and swiping left/right.
