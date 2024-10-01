# Magisk on WSA (with Google Apps)

## Features

- Integrate Magisk and OpenGApps in a few clicks within minutes
- No Linux environment required for integration
- Keep each build up to date
- Support both ARM64 and x64
- Support all OpenGApps variants except for aroma (aroma does not support x86_64, please use super instead)
- Fix VPN dialog not showing (use our [VpnDialogs app](https://github.com/LSPosed/VpnDialogs))
- Unattended installation
- Automatically activates developers mode in Windows 11
- Update to new version while preserving data with one-click script
- Merged all language packs
- Support managing start menu icons (manually installing [WSAHelper](https://github.com/LSPosed/WSAHelper/releases/latest) to use this feature)

## Video Guide

https://user-images.githubusercontent.com/5022927/145696886-e13ebfc1-ff25-4410-893e-d3e517af70ea.mp4

## Text Guide

1. Star (if you like) and fork this repo (keep it PUBLIC, private repo is not supported)
1. Go to the **Action** tab in your forked repo
    ![Action Tab](https://docs.github.com/assets/images/help/repository/actions-tab.png)
1. In the left sidebar, click the **Build WSA** workflow.
    ![Workflow](https://docs.github.com/assets/images/actions-select-workflow.png)
1. Above the list of workflow runs, select **Run workflow**
    ![Run Workflow](https://docs.github.com/assets/images/actions-workflow-dispatch.png)
1. Select the version of Magisk and select the [OpenGApps variant](https://github.com/opengapps/opengapps/wiki#variants) (none is no OpenGApps) you like, select the root solution (none means no root), select WSA version and its architecture (mostly x64) and click **Run workflow**
    ![Run Workflow](https://docs.github.com/assets/images/actions-manually-run-workflow.png)
1. Wait for the action to complete and download the artifact **DO NOT download it via multithread downloaders like IDM or ADM**
    ![Download](https://docs.github.com/assets/images/help/repository/artifact-drop-down-updated.png)
1. Unzip the artifact
    - The size shown in the webpage is uncompressed size and the zip you download will be compressed. So the size of the zip will be much less than the size shown in the webpage.
1. Right-click `Install.ps1` and select `Run with PowerShell`
    - If you previously have a MagiskOnWSA installation, it will automatically uninstall the previous while **preserving all userdata** and install the new one, so don't worry about your data.
    - If you have an official WSA installation, you should uninstall it first. (In case you want to preserve your data, you can backup `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx` before uninstallation and restore it after installation.) (If you want to restore the icons to start menu, please install and use [WSAHelper](https://github.com/LSPosed/WSAHelper/releases/latest).)
    - If the popup windows disappear **without asking administrative permission** and WSA is not installed successfully, you should manually run `Install.ps1` as administrator:
        1. Press `Win+x` and select `Windows Terminal (Admin)`
        2. Input `cd "{X:\path\to\your\extracted\folder}"` and press `enter`, and remember to replace `{X:\path\to\your\extracted\folder}` including the `{}`, for example `cd "D:\wsa"`
        3. Input `PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1` and press `enter`
        4. The script will run and WSA will be installed
        5. If this workaround does not work, your PC is not supported for WSA
1. Magisk/Play store will be launched. Enjoy by installing LSPosed-zygisk with zygisk enabled or Riru and LSPosed-riru

## FAQ

- Actions workflow task `Delete workflow runs` run Failed

    Check workflow permissions, should be `Read and write permissions`

     ![permissions](https://user-images.githubusercontent.com/40033067/168649322-dadaafc9-dd31-4922-afe1-8aa933b7b036.png)

     Read the [Github Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-default-github_token-permissions) to find out how to change this setting

- Why should we delete old workflow runs?

    Keeping old workflow runs can take up a lot of storage resources and is suspected to be abusive, which can lead to banning.
- Can I delete the unzipped folder?

    No.
- Why the size of the zip does not match the one shown?

   The zip you downloaded is compressed and Github is showing the uncompressed size.
- How can I update WSA to new version?


