---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Module
ms.openlocfilehash: acea38b0eebc58dafda0ab58b91dc6a70ffffd3b
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2017
---
# <a name="save-module"></a>Save-Module

Speichert ein Modul lokal, ohne es zu installieren

## <a name="description"></a>Beschreibung

Das Cmdlet „Save-Module“ speichert ein Modul aus dem angegebenen Repository zur Prüfung lokal. Das Modul wird nicht installiert.

## <a name="cmdlet-syntax"></a>Cmdlet-Syntax
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Save-Module](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a>Beispiele für Befehle

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath


# Save a specific prerelease version of a module to C:\MySavedModuleLocation
Save-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -Path C:\MySavedModuleLocation -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -Path C:\MySavedModuleLocation -AllowPrerelease



```

