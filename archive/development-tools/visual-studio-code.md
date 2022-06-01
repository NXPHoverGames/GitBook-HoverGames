---
description: Guide to installing and configuring Visual Studio Code for HoverGames.
---

# Visual Studio Code

{% hint style="warning" %}
This page is **archived**. You are probably looking for the [development tools](../../developerguide/tools/) page.
{% endhint %}

## Installing Visual Studio Code

{% hint style="danger" %}
This page is outdated. There will be issues when you follow the instructions below. We currently do not support Visual Studio Code until we are able to create a fully functional setup again.&#x20;

Better instructions are available in the [PX4 Developer Guide](https://dev.px4.io/master/en/setup/vscode.html).
{% endhint %}

Visual Studio Code is available for free for Windows, MacOS and Linux. In this guide, we will install the Linux version inside our Ubuntu virtual machine. Please download the appropriate package from the website. For Ubuntu, we need the `.deb` file.

{% embed url="https://code.visualstudio.com/" %}

You should be able to install Visual Studio Code by double clicking the `.deb` file you just downloaded. After installation has finished, Visual Studio Code should be available in your applications menu. Just search for the name and it will show up.

## Editor configuration

Start Visual Studio Code. Click the "Extensions" icon in the bar on the left. Install the "C/C++" extension by Microsoft, and the "Astyle" extension by Chieh Yu. You also need to open a terminal window and install the Astyle and openOCD applications through your package manager, using the following command:

`sudo apt install astyle openocd`

The packages might already be installed and up-to-date. That's fine.

![](<../../.gitbook/assets/image (133).png>)

We also need to change some editor settings. Go to the "File" tab, look for "Preferences" and then go to "Settings". The fastest way to edit the settings is to edit the `settings.json` file directly. You can easily open it using the icon with the two curly brackets on the top right. It's probably still empty. Copy the following settings, and make sure to save the file:

{% code title="settings.json" %}
```
{
    "editor.formatOnSave": true,
    "editor.renderWhitespace": "boundary",
    "editor.minimap.enabled": false,
}
```
{% endcode %}

![](<../../.gitbook/assets/image (136).png>)

We also need to download some additional configuration files for openOCD. Enter the following commands:

`cd ~/src`\
`wget 'https://bitbucket.org/!api/2.0/snippets/nxp-drone/rezdy7/files/nxphlite-v3.cfg'`\
`wget 'https://bitbucket.org/!api/2.0/snippets/nxp-drone/rezdy7/files/openocd.sh'`\
`chmod +x openocd.sh`

## Setup a PX4 project

Go to "File" and then "Open folder" and open the `/home/hovergames/src/Firmware` folder with the PX4 sources.

We again need to change some settings, this time specific to the workspace. Again, go to "File", "Preferences", "Settings". Now, first click the "Workspace Settings" tab instead of "User Settings". If you now click the icon with the curly brackets, you will get a different settings.json file. Add the following settings into your file, and make sure to save:

{% code title="settings.json" %}
```
{
    "astyle.astylerc": "${workspaceRoot}/Tools/astyle/astylerc",
    "C_Cpp.formatting": "Disabled",
    "files.watcherExclude": {
        "**/.git/objects/**": true,
        "**/.git/subtree-cache/**": true,
        "**/.ci/**": true,
        "**/build/**": true,
        "**/cmake/**": true,
        "**/Documentation/**": true,
        "**/integrationtests/**": true,
        "**/launch/**": true,
        "**/mavlink/**": true,
        "**/msg/**": true,
        "**/platforms/**": true,
        "**/posix-configs/**": true,
        "**/ROMFS/**": true,
        "**/test/**": true,
        "**/test_data/**": true,
        "**/Tools/**": true,
    },
}

```
{% endcode %}

![](<../../.gitbook/assets/image (137).png>)

## Building and uploading the firmware

Go to "View" and then "Terminal" (or press `Ctrl` and `` ` ``). Inside the terminal, you can enter the following command to build the code:

`make nxp_fmuk66-v3_default`

After the build is (succesfully) finished, you can upload it to the FMU board when you have it plugged in with USB, using this command:

`make nxp_fmuk66-v3_default upload`

## Configuring for debugging

{% hint style="warning" %}
Pop-ups might start appearing about recommended extensions and settings. Just ignore those, and follow these instructions. You might break the setup when you just use the recommended settings.
{% endhint %}

The default PX4 build enables compiler optimizations for performance reasons. For debugging however this can be confusing, because the compiler sometimes changes the program flow and it eliminates variables, which can be pre-computed. Therefore it is recommended to debug without optimizations, which can be achieved with the compiler flag `O0`.

First, we need to download some additional configurations for debugging. Use the following commands to download and place them in the right folders:

`cd ~/src/Firmware/.vscode`

`wget 'https://bitbucket.org/!api/2.0/snippets/nxp-drone/dezXyj/e8aa8ad13810b5198195bf4b7d89d3debd2b2a6b/files/launch.json'`

`mv launch.json.1 launch.json`

`wget 'https://bitbucket.org/!api/2.0/snippets/nxp-drone/dezXyj/e8aa8ad13810b5198195bf4b7d89d3debd2b2a6b/files/tasks.json'`

`mv tasks.json.1 tasks.json`

## Start debugging

When we start debugging, we have to start with and clean build and recompile with the `O0` compiler flag. Use the `make clean` command in the integrated terminal to clean the project. Go to the debug icon in the bar on the left. Make sure you have the debugger plugged in, and then enter the following command in the integrated terminal:

`../openocd.sh debug-server`

Then, at the top left, select "flash and start" when recompiled firmware still has to be uploaded to the board, otherwise, just chose "start" and click the green play button to start your debug session.

![](<../../.gitbook/assets/image (139).png>)

##
