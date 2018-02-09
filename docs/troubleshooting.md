<!--
Copyright © Microsoft Corporation
All rights reserved.
Creative Commons Attribution 4.0 License (International): https://creativecommons.org/licenses/by/4.0/legalcode
-->

# Troubleshooting

## Tool Requirements

| Tool | Problem | Resolution |
|------|---------|------------|
| Visual Studio 2017 | When trying to install the Visual Studio Live Share VSIX, the VSIX installer cannot find a version of Visual Studio to use.  | Visual Studio Live Share requires VS 2017 15.6 Preview 3+ for both hosts and guests. Download the latest [preview version of VS](http://visualstudio.com/vs/preview) and retry. |
| Visual Studio Code | Installing the extension from the marketplace installs it in the stable version of VS Code instead of Insiders. | Start VS Code Insiders, click on the "extensions" tab, search for "VS Live Share" and install from there. |
| Visual Studio Code | You get an error when trying to use Visual Studio Live Share with VS Code Linux. | VS Code Linux is not currently supported. [Upvote this feature](https://github.com/MicrosoftDocs/live-share/issues/24) if you'd like to see support added. |
| Visual Studio Code | Uninstalling the Live Share extension never completes. | Restart VS Code and try again. |

## Sign in

The following are troubleshooting tips for sign in problems.

| Tool | Problem | Resolution / Workaround |
|------|---------|------------|
| VS | You need to sign into VS Live Share with a different identity than you use to sign into Visual Studio. | Go to Tools > Options > Live Share > User account to select or sign into an alternate account. |
| VS Code | When signing in, the browser window appears and you are able to sign in, but once complete Visual Studio Code still shows that it is not signed in. | After signing in, click "Having trouble?" and follow the directions to enter a temporary user code into the tool. |
| VS Code | When clicking sign-in or joining from a link when not signed in, no browser window appears to allow you to sign in. | Go to https://insiders.liveshare.vsengsaas.visualstudio.com/auth/login and sign in. After signing in, click "Having trouble?". Finally, follow the directions to enter a temporary user code into the tool. |
| All | You are getting a timeout or error about not being able to connect. | See [connectivity troubleshooting](#connectivity). |

## Sharing and Joining

The following are troubleshooting tips for sign in problems.

| Tool | Problem | Resolution / Workaround |
|------|---------|------------|
| All | You have [signed up](http://aka.ms/vsls-signup) for the private preview but are getting an error about not being accepted when you try to share. | Visual Studio Live Share is currently in a limited, private preview. During the preview period, you will need to be accepted into the program to share but not to join. Anyone may install the extension and join an accepted "host" as a "guest." Acceptances will occur in waves over the preview period and you will be notified once accepted. | 
| All | You are getting a timeout or error about not being able to connect. | See [connectivity troubleshooting](#connectivity). |
## Connectivity

The information below can help you troubleshoot if you're having problems related to connectivity or timeouts when signing in, sharing, or joining. 

As outlined in [getting started](getting-started.md#changing-the-connection-mode), different connection modes have different requirements to function so there are a few different potential issues going on.

| Mode | Requirements | Troubleshooting |
|------|----------------|----------------------|
| All | Access to *.liveshare.vsengsaas.visualstudio.com on port 80/443 | Ensure your corporate or personal network firewall allows you to connect to this domain. Enter http://insiders.liveshare.vsengsaas.visualstudio.com in a browser and verify you land at the VS Live Share home page. |
| Auto | Auto-switches. See direct and relay modes. | Switch to direct or relay mode to troubleshoot. |
| Direct | A port in the range 5990 - 5999 needs to be open on the host's machine and guests need to be able to directly connect to each other. (See [this feature request](https://github.com/MicrosoftDocs/live-share/issues/60) for a proposed improvement.) | Verify "vsls-agent" is not blocked by your desktop firewall software for this port range and that you can ping one another. While Windows and other desktop software should prompt you the first time the agent starts up, we have seen instances where group policies prevent this from happening and you will need to [manually add the entry](#manually-adding-a-firewall-entry-for-direct-mode). |
| Relay | Access to *.servicebus.windows.net on port 80/443. | Ensure your corporate or personal network firewall allows you to connect to this domain. |

Specific examples of issues:

| Problem | Possible Cause | 
|------|----------------|
| You are unable to sign into VS Live Share | You cannot access the internet or access to *.liveshare.vsengsaas.visualstudio.com on port 80/443 is blocked by your personal or corporate firewall. | 
| You are in direct mode and able to sign into VS Live Share but are notified of a timeout when either sharing or joining. | The guest and host cannot directly connect. Try [auto or relay mode](getting-started.md#changing-the-connection-mode). |
| You are in relay mode and able to sign into VS Live Share but are notified of a timeout when either sharing or joining. | Access to *.servicebus.windows.net on port 80/443 is blocked is blocked by your personal or corporate firewall. Try [direct mode](getting-started.md#changing-the-connection-mode). |
| You are in auto mode and able to sign into VS Live Share but are notified of a timeout when either sharing or joining. | Either you are having trouble with both direct and relay mode or there is a bug with auto mode detecting the right connection type. If you are able to [switch to direct or relay mode](getting-started.md#changing-the-connection-mode) and connect, please [raise a bug](../CONTRIBUTING.md). |

## Workaround: Manually adding a firewall entry for direct mode

If you want to use direct mode but found that your firewall does not have an entry for it, you can add it from one of the following locations:

VS Code (substitue **VERSION** for the extension version):

- **Windows:** %USERPROFILE%\\.vscode-insiders\extensions\ms-vsliveshare.vsliveshare-*VERSION*\dotnet_modules\win7-x86\vsls-agent.exe
- **macOS:** $HOME/.vscode-insiders/extensions/ms-vsliveshare.vsliveshare-*VERSION*/dotnet_modules/osx.10.10-x64/vsls-agent

Visual Studio:  
- Run a search for vsls-agent.exe in your VS install locaiton under **IDE\Extensions**
- The VS install location is typically C:\Program Files (x86)\Microsoft Visual Studio\Preview\\*EDITION* where **EDITION** is Community, Enterprise, etc 

## More Info

- [Getting started and managing collaboration sessions](getting-started.md)
- [Visual Studio enabled features](collab-vs.md)
- [Visual Studio Code enabled features](collab-vscode.md)
- [Summary of language and platform support](platform-support.md)
- [FAQ](http://aka.ms/vsls-faq)