---
ms.mktglfcycl: manage
ms.sitesec: library
ms.author: brianlic
author: brianlic-msft
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: Microsoft.Windows.Appx.PackageManager.Commands.dll-Help.xml
keywords: powershell, cmdlet
manager: alanth
ms.date: 2016-12-20
ms.prod: w10
ms.technology: powershell-windows
ms.topic: reference
online version: 
schema: 2.0.0
title: Add-AppxPackage
ms.assetid: 40B54C64-C3EB-4898-AE19-CDD5CA3BD70E
---

# Add-AppxPackage

## SYNOPSIS
Adds a signed app package to a user account.

## SYNTAX

### AddSet (Default)
```
Add-AppxPackage [-Path] <String> [-DependencyPath <String[]>] [-ForceApplicationShutdown]
 [-ForceTargetApplicationShutdown] [-InstallAllResources] [-Volume <AppxVolume>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### RegisterSet
```
Add-AppxPackage [-Path] <String> [-DependencyPath <String[]>] [-Register] [-DisableDevelopmentMode]
 [-ForceApplicationShutdown] [-ForceTargetApplicationShutdown] [-InstallAllResources] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UpdateSet
```
Add-AppxPackage [-Path] <String> [-DependencyPath <String[]>] [-ForceApplicationShutdown]
 [-ForceTargetApplicationShutdown] [-InstallAllResources] [-Update] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RegisterByPackageFullNameSet
```
Add-AppxPackage [-Register] -MainPackage <String> [-DependencyPackages <String[]>] [-ForceApplicationShutdown]
 [-ForceTargetApplicationShutdown] [-InstallAllResources] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Add-AppxPackage** cmdlet adds a signed app package to a user account.
An app package has an .appx file name extension.
Use the *DependencyPath* parameter to add all other packages that are required for the installation of the app package.

You can use the *Register* parameter to install from a folder of unpackaged files during development of Windows® Store apps.

To update an already installed package, the new package must have the same package family name.

## EXAMPLES

### Example 1: Add an app package
```
PS C:\> Add-AppxPackage -Path "C:\Users\user1\Desktop\MyApp.appx" -DependencyPath "C:\Users\user1\Desktop\winjs.appx"
```

This command adds an app package that the package contains.

### Example 2: Add a disabled app package in development mode
```
PS C:\> $ManifestPath = (Get-AppxPackage -Name "*WindowsCalculator*").InstallLocation + "\Appxmanifest.xml"
PS C:\> Add-AppxPackage -Path $ManifestPath -Register -DisableDevelopmentMode
```

This command gets the full path of the package manifest file of an installed Windows Store app, and then registers that package.
You can use *DisableDevelopmentMode* to register an application that is staged by the **StagePackageAsync** API, has been disabled, or has become corrupted during testing.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DependencyPackages
Specifies the dependency package full name or dependency package bundle full name to be registered.

```yaml
Type: String[]
Parameter Sets: RegisterByPackageFullNameSet
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -DependencyPath
Specifies an array of file paths of dependency packages that  are required for the installation of the app package.
The app package has an .appx or .appxbundle file name extension.
You can specify the paths to more than one dependency package.

```yaml
Type: String[]
Parameter Sets: AddSet, RegisterSet, UpdateSet
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableDevelopmentMode
Indicates that this cmdlet registers an existing app package installation that has been disabled, did not register, or has become corrupted.
Use the current parameter to specify that the manifest is from an existing installation, and not from a collection of files in development mode.
You can also use this parameter to register an application that the [Package Manager API](http://go.microsoft.com/fwlink/?LinkId=245447) has staged.
Use the *Register* parameter to specify the location of the app package manifest .xml file from the installation location.

```yaml
Type: SwitchParameter
Parameter Sets: RegisterSet
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForceApplicationShutdown
Indicates that this cmdlet forces all active processes that are associated with the package or its dependencies to shut down.
If you specify this parameter, do not specify the *ForceTargetApplicationShutdown* parameter.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForceTargetApplicationShutdown
Indicates that this cmdlet forces all active processes that are associated with the package to shut down.
If you specify this parameter, do not specify the *ForceApplicationShutdown* parameter.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstallAllResources
Indicates that this cmdlet forces the deployment of all resource packages specified from a bundle argument.
This overrides the resource applicability check of the deployment engine and forces staging of all resource packages, registration of all resource packages, or staging and registration of all resource packages.
This parameter can only be used when specifying a resource bundle or resource bundle manifest.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MainPackage
Specifies the main package full name or bundle full name to register.

```yaml
Type: String
Parameter Sets: RegisterByPackageFullNameSet
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the file path of the app package.
An app package has an .appx or .appxbundle file name extension.

```yaml
Type: String
Parameter Sets: AddSet, RegisterSet, UpdateSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Register
Indicates that this cmdlet registers an application in development mode.
You can use development mode to install applications from a folder of unpackaged files.
You can use the current parameter to test your Windows® Store apps before you deploy them as app packages.
To register an existing app package installation, you must specify the *DisableDevelopmentMode* parameter and the *Register* parameter.
In order to specify dependency packages, specify the *DependencyPath* parameter and the *DisableDevelopmentMode* parameter.

```yaml
Type: SwitchParameter
Parameter Sets: RegisterSet
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: SwitchParameter
Parameter Sets: RegisterByPackageFullNameSet
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Update
Specifies that the package being added is a dependency package update.
A dependency package is removed from the user account when the parent app is removed.
If you do not use this parameter, the package being added is a primary package and is not removed from the user account if the parent app is removed.
To update an already installed package, the new package must have the same package family name.

```yaml
Type: SwitchParameter
Parameter Sets: UpdateSet
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Volume
Specifies the **AppxVolume** object to which to stage the package.
The volume also specifies the default location for user **AppData**.

```yaml
Type: AppxVolume
Parameter Sets: AddSet
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

### System.IO.FileInfo

## OUTPUTS

### None

## NOTES

## RELATED LINKS

[Package Manager API](http://go.microsoft.com/fwlink/?LinkId=245447)

[How to Add and Remove Apps](http://go.microsoft.com/fwlink/?LinkID=231020)

[Get-AppxPackage](./Get-AppxPackage.md)

[Get-AppxPackageManifest](./Get-AppxPackageManifest.md)

[Move-AppxPackage](./Move-AppxPackage.md)

[Remove-AppxPackage](./Remove-AppxPackage.md)

