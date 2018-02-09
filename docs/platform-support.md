
<!--
Copyright © Microsoft Corporation
All rights reserved.
Creative Commons Attribution 4.0 License (International): https://creativecommons.org/licenses/by/4.0/legalcode
-->

# Language and platform support

Visual Studio Live Share's features are intended to work across a diverse landscape of languages and application platforms. However, given the sheer number of variations, some platforms and languages are more complete than others. This document covers the current known state of a number of popular languages and platforms for currently supported features.

See a language or platform you need? Want to add one you don't see? [Vote here.](https://github.com/MicrosoftDocs/live-share/issues/12)

**Contents**

- [VS Code](#visual-studio-code)
  - [Languages](#languages)
  - [Platforms](#platforms)
- [Visual Studio](#visual-studio)
  - [Languages](#languages-1)
  - [Platforms](#platforms-1)


## Visual Studio Code

All languages / platforms have same file intellisense (when the respective extension is installed), as well as colorization and co-editing support. The lists below covers advanced features currently without complete, universal support:

### Languages

| Language | Project-wide language services | Co-Debugging |
|----------|--------------------------------|--------------|
| JavaScript / TypeScript | ✅ | ✅ <sup>3</sup> |
| C# | ✅ | ✅ | |
| CSHTML | *N/A* <sup>1</sup> | ✅
| HTML | *N/A* | <sup>2</sup> |
| CSS | *N/A* | *N/A* |
| Python | | ✅ <sup>4 *(Win only)*</sup> |
| Markdown | *N/A* | *N/A* |
| Java | | ✅ | |
| Go | | ✅ | |
| C++ | | ✅ | |
| PowerShell | *N/A* | ✅ | | |
| Bash | *N/A* | ✅ | |
| Erlang | | | | |
| Haskell | | ? |
| PHP | | ✅ |
| Reason/OCaml | | *N/A* <sup>5</sup> |
| Ruby | | ✅ | |
| Rust | | *N/A* <sup>5</sup> |
| Swift | | *N/A* <sup>5</sup> |
| SQL / T-SQL | *N/A* | |

<sup>1</sup> No CSHTML support in C# extension.<br />
<sup>2</sup> Embedded JavaScript in HTML is supported when doing client debugging.<br />
<sup>3</sup> JavaScript / TypeScript debugging for Node or browser.<br />
<sup>4</sup> Bug: Python debugger support on Mac has a known issue. Debugging on Windows works. [Vote (👍) here.](https://github.com/MicrosoftDocs/live-share/issues/62)<br />
<sup>5</sup> The respective extension for VS Code doesn't currently support debugging. As soon as it does, we will investigate adding co-debugging support to it. <br />
<sup>?</sup> Not yet validated.

### Platforms

| App/platform type | Co-debugging | App sharing |
|-------------------|--------------|-------------|
| Web app / API (Back-end) | ✅ | ✅ <sup>1</sup> |
| Web app (Front-end) | ✅ <sup>2</sup> | ✅ <sup>3</sup> |
| Azure Functions | ✅ | ✅ <sup>1</sup> |
| [Visual Studio Connected Environment for AKS](http://landinghub.visualstudio.com/vsce) | ✅ | ✅ <sup>1</sup> |
| Markdown | *N/A* | ✅ <sup>6</sup> |
| Databases | <sup>5</sup> | ✅ <sup>1</sup> |
| Console / CLI | ✅ | <sup>4</sup> |
| VS Code extensions | | |
| Mobile (React Native) |  | ✅ <sup>1,8</sup> |
| Mobile (Cordova) | ✅ | ✅ <sup>1,7</sup> |
| Mobile (Native) |  | |
| Desktop (Electron/native) | ✅ | |
| Games (Unity) | ? | |

<sup>1</sup> Via [share local server](collab-vscode.md#sharing-a-local-server).<br />
<sup>2</sup> Debugging occurs against the host's browser rather than guest.<br />
<sup>3</sup> By sharing back-end.<br />
<sup>4</sup> Would be enabled via shared terminals. [Vote (👍) here.](https://github.com/MicrosoftDocs/live-share/issues/41)<br />
<sup>5</sup> Debugging database stored procs is not currently supported <br />
<sup>6</sup> Via "preview". However, images do not appear due to known issue. [Vote (👍) here.](https://github.com/MicrosoftDocs/live-share/issues/61)<br />
<sup>7</sup> Cordova apps can be shared via the the "browser" platform<br />
<sup>8</sup> React Native apps can be shared via Expo and [share local server](collab-vscode.md#sharing-a-local-server).<br />
<sup>?</sup> Not yet validated.

## Visual Studio

While most languages have some single file Intellisense support, there are some caveats outlined below. All languages/platforms support co-editing. The remainder of the list covers advanced features features currently without complete, universal support:

### Languages

| Language | Single-file language services | Project-wide language services | Co-Debugging |
|----------|-------------------------------|--------------------------------|--------------|
| C# | ✅ | ✅ | ✅ | 
| CSHTML | ✅  <sup>1</sup> | | ✅ |
| ASPX | ✅ <sup>1</sup> |  | ✅ |
| HTML | ✅ | *N/A* | <sup>3</sup> |
| CSS | ✅ | *N/A* | *N/A* |
| JavaScript / TypeScript | ✅ | ✅ | ✅ <sup>4</sup> |
| C++ | ✅ | | ✅ | 
| Python | ✅ <sup>2</sup> | | ✅ |
| Markdown | ✅ | *N/A* | *N/A* |
| PowerShell | ✅ | *N/A* | <sup>7</sup> | 
| VB.NET | ✅ | | ✅ |
| VBHTML | ✅ <sup>1</sup> | | ✅ |
| XAML | ✅ | *N/A* | <sup>6</sup> | 
| SQL / T-SQL | ✅ | *N/A* | |
| F# | ✅ <sup>2</sup>| | ✅ |
| R | <sup>8</sup> | *N/A* | ✅ |

<sup>1</sup> Gap: CSHTML, VBHTML, and ASPX have a known issues around embedded C#/VB support given code-behind C#/VB files are not resolved due to full intellisense not being implemented. [Vote (👍) here on CSHTML/VBHTML.](https://github.com/MicrosoftDocs/live-share/issues/59) [Vote (👍) here on ASPX.](https://github.com/MicrosoftDocs/live-share/issues/70)<br />
<sup>2</sup> Gap: Guests see errors for valid types, namespaces, and modules defined outside of the current file due to full intellisense not being implemented. [Vote (👍) here for F#.](https://github.com/MicrosoftDocs/live-share/issues/64) [Vote (👍) here for Python.](https://github.com/MicrosoftDocs/live-share/issues/63)<br />
<sup>3</sup> Embedded JavaScript in HTML is supported when doing client debugging.<br />
<sup>4</sup> JavaScript / TypeScript debugging for Node or browser.<br />
<sup>6</sup> Though debugging XAML itself is technically N/A, debugging code-behind is supported.<br />
<sup>7</sup> Gap: Debugging PowerShell projects hangs VS for host after sharing. [Vote (👍) here](https://github.com/MicrosoftDocs/live-share/issues/71) <br />
<sup>8</sup> Gap R language service errors on the guest side on join and after every newline. Not supported. [Vote (👍) here.](https://github.com/MicrosoftDocs/live-share/issues/72)<br />

### Platforms

| App/platform type | Co-debugging | App sharing |
|-------------------|--------------|-------------|
| Web app / API (Back-End) | ✅ | ✅ <sup>1</sup> |
| Web app (Front-end) | ✅ <sup>2</sup> | ✅ <sup>3</sup> |
| Azure Data Lake | ? | |
| Azure Functions | ? | |
| Azure Service Fabric | ? | |
| Azure Stream Analytics | ? | |
| [Visual Studio Connected Environment for AKS](http://landinghub.visualstudio.com/vsce) | ? | ✅ <sup>1</sup> |
| Databases | <sup>4</sup> | ✅ <sup>5</sup> |
| Console / CLI | ✅ | |
| Desktop (WinForms) | ✅ | |
| Desktop (WPF) | ✅ | |
| Universal Windows Platform | ✅ |  |
| Mobile (Xamarin) | ? |  |
| Mobile (Cordova) | ? | ? |
| Mobile (Native C++) | ? |  |
| Games (Win32 C++) | ? |  |
| Games (Unity) | ? | |
| Office / Sharepoint | ? | |
| VS Extensions | ✅ |  |
| Linux (C++) | ? | |

<sup>1</sup> Via [share local server](collab-vs.md#sharing-a-local-server). ASP.NET Web Apps can also use [automatic web app sharing](collab-vs.md#automatic-web-app-sharing-during-debugging).<br />
<sup>2</sup> Debugging occurs against the host's browser rather than guest.<br />
<sup>3</sup> By sharing back-end.<br />
<sup>4</sup> Debugging database stored procs is not currently supported <br />
<sup>5</sup> Via [share local server](collab-vs.md#sharing-a-local-server). <br />
<sup>?</sup> Not yet validated.

## More information

- [Getting started and managing collaboration sessions](getting-started.md)
- [Visual Studio enabled features](collab-vs.md)
- [Visual Studio Code enabled features](collab-vscode.md)
- [Troubleshooting](troubleshooting.md)
- [FAQ](http://aka.ms/vsls-faq)
