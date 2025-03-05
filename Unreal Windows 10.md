# Unreal for Windows 10

If you are using Windows 10 you might have some issues opening a C++ Unreal project. If you are getting this message "could'nt be compiled. Try rebuilding from source manually" when opening your project
try following these steps to fix.

## Visual Studio
Ensure you have every component necessary for Unreal projects downloaded.

Below is a link to Unreal documentation which lists the necessary components. You can download these in Visual Studio Installer by pressing Modify.

https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine

Notes:
- Universal Windows Platform development has changed name. I believe it is now called "WinUI application development"
- For Windows 10 please use the exact recommended version of MSVC, not necessarily the newest one. For Unreal 5.4 this is **'MSVC v143 - VS 2022 C++ x64/x86 build tools (v14.38-17.8)** 
- Make sure you have Windows 10 SDK.
- Make sure you have Unreal Engine Installer.

Try building/opening the project it might work now.

**Building**

To build your project:

- In your project folder, delete 'Binaries', 'Intermediate' and 'Saved' folders.
- Right click on your project and press 'Generate visual studio project files' 
- Open the .sln file made using your preferred IDE, I am using Rider. (visual studio, rider)
- Build project.


## Editing header file 

If your project is still not opening follow these steps:

Locate 'yourprojectname.h' file. At the very top of the file add this:

```
#ifndef __has_feature
#define __has_feature(x) 0
#endif
```

Then find 'yourprojectnameEditor.Target.cs' and add:

```
'IncludeOrderVersion = EngineIncludeOrderVersion.Latest;'
```

Add this inside your constructor.

Try building your project. Hopefully it should work now.



