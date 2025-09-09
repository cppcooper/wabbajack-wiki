# Compilation Settings

Compilation itself is very straightforward and similar to installation: you let Wabbajack run and hope it finishes successfully! The key to make it run successfully is having a "Wabbajack-compliant" MO2 setup which you can set up by following the recommendations from the previous sections.

## Find or Generate Your `.compiler_settings`

-   Click on the three dots next to the `Compiler Settings` field.
-   In the file selection window that opens:
    -   If it is your first time compiling a list, navigate to `profiles/{profile_name}/` and select `modlist.txt`. This will generate the required `.compiler_settings` file for this and future compilation.
    -   If you have already used Wabbajack with the MO2 instance you want to compile with or are using [ative-Game-Installer (Installers not using MO2)](<Native-Game-Installer%20-%20(Installers%20not%20using%20MO2).md>), change the file extension from `MO2 Modlist (.txt)` to `Compiler Settings File (.compiler_settings)` and select the `ModlistName.compiler_settings` file.

## Download Location

The download location is the path to the folder where all your archives and `.meta` files are located.

## Output Location

The output location is the path to the folder where your modlist's `.wabbajack` file will be written.

## Wabbajack Compilation Configuration Editor

In Wabbajack, select _Create a Modlist_ to navigate to the configuration screen. Here you can configure some metadata for your modlist which will later be viewable by the user.

| Field               | Description                                                                                                                 | Notes                                                                                                                                                                                                                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Modlist Name        | **REQUIRED:** Name of your modlist                                                                                          |                                                                                                                                                                                                                                                                                                         |
| Version             | **REQUIRED:** Current Version                                                                                               | Wabbajack modlists **must** comply with the [.NET Version Class](https://learn.microsoft.com/en-us/dotnet/api/system.version?view=net-7.0#remarks) `major.minor[.build[.revision]]` making `0.1.19.1` a valid version Example. Don't use Text or Special Characters in your version!                                                                                                                                           |
| Author              | Modlist author--your name or alias                                                                                          | Should be your name in original modlists and/or the name of the original modlist author if you adapted a non-WJ modlist to WJ                                                                                                                                                                           |
| Description         | Modlist description (max 700 charcters)                                                                                     |                                                                                                                                                                                                                                                                                                         |
| Image               | Modlist image                                                                                                               | Aspect ratio should be 16:9 for best results                                                                                                                                                                                                                                                            |
| Website             | **REQUIRED:** Website URL                                                                                                   | Link to a Website/Readme                                                                                                                                                                                                                                                                                |
| Readme              | **REQUIRED:** Readme URL                                                                                                    | Link to the readme                                                                                                                                                                                                                                                                                      |
| NSFW                | NSFW Checkbox                                                                                                               | Only really needed for official modlists as our galleries have the option to hide NSFW modlists                                                                                                                                                                                                         |
| Publish Update      | Publish Update Checkbox                                                                                                     | If you completed [Getting CDN Access](../wabbajack_cdn_and_gallery_access/Getting%20CDN%20Access.md) and [Adding a Custom Repository to Wabbajack](../wabbajack_cdn_and_gallery_access/Adding%20a%20Custom%20Repository%20to%20Wabbajack.md) you can use this option to automatically publish your list |
| MachineUrl          | `machineURL` of the modlist required for the `Publish Update` option                                                        | [Adding a Custom Repository to Wabbajack](../wabbajack_cdn_and_gallery_access/Adding%20a%20Custom%20Repository%20to%20Wabbajack.md) Is referencing this field with its `JohnsLists/JohnsSkyrimMakeover` Example                                                                                         |
| No Match Include    | Adds folders to a list from which all content that can't be matched to a source should still be included                    | Useful for custom patches or generated files                                                                                                                                                                                                                                                            |
| Include             | Adds files and folders to a list which will be included with the .wabbajack file                                            | **DO NOT USE ON DOWNLOADED MODS** as this would result in inlining the mod into the `.wabbajack` file and (unacceptably) distributing that mod. Can lead to large `.wabbajack` files if used unsparingly                                                                                                |
| Ignore              | Adds files and folders to a list that will be ignored and therefore will not be part of final installations                 | Useful for mods and tools you use during development you don't want included in the final installation                                                                                                                                                                                                  |
| Other Profiles      | Adds profile folders to a list for other MO2 profiles you want to include in the final installation                         | Useful for performance, or content profiles                                                                                                                                                                                                                                                             |
| Always Enabled Mods | Adds mod folders to a list of mods that will be included in your list no matter if they are enabled (active in game) or not | Wabbajack will normally ignore all mods you disabled in MO2 but there are some cases where you might want to give some choice to the end user and want to have the mod included                                                                                                                         |

## Other Games
Some modlists may want to make use of files from other, related games. 

An example being - Fallout 4 VR may want to use the DLC from Fallout 4, and the same for Skyrim VR and Skyrim AE DLC.

If you open up the <modlistname>.compiler_settings file in your modlist directory, with a text editor, you will see a field called "OtherGames"
now check the Wabbajack code for which games can source from other games (here)[https://github.com/wabbajack-tools/wabbajack/blob/main/Wabbajack.DTOs/Game/GameRegistry.cs] 

For example,  in that code you will see that SkyrimVR has a field for "cansourcefrom" which points to "SkyrimSpecialEdition". 

If you were to put "SkyrimSpecialEdition" or "Fallout4" in your SkyrimVR or Fallout4 VR compiler_settings file in the "OtherGames" field , then Wabbajack will be able to scan that directory for required files, both in compilation and on the user install side of things.

like so :

```
"OtherGames": [
    "SkyrimSpecialEdition"
  ],
```

If you want to add a "cansourcefrom" to any of the games Wabbajack supports, please propose that on the Wabbajack Github [here](https://github.com/wabbajack-tools/wabbajack)

## Compilation Errors

You will likely get a ton of errors during your first compilation, which is to be expected. We highly recommend you join our [Discord server](https://discord.gg/wabbajack) and go to the `#modlist-development-help` channel for help.
