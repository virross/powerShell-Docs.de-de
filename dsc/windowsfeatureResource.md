---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „WindowsFeature“"
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a>DSC-Ressource „WindowsFeature“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass Rollen und Features einem Knoten hinzugefügt oder entfernt werden.

## <a name="syntax"></a>Syntax

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Rolle oder des Features an, die/das hinzugefügt oder entfernt werden soll. Dies ist identisch mit der __Name__-Eigenschaft aus dem Cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) und nicht mit dem Anzeigenamen der Rolle oder des Features.| 
| Credential| Gibt die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rolle oder des Features an.| 
| Ensure| Gibt an, ob die Rolle oder das Feature hinzugefügt wird. Um sicherzustellen, dass die Rolle oder das Feature hinzugefügt wird, legen Sie diese Eigenschaft auf „Present“ fest. Um sicherzustellen, dass die Rolle oder das Feature entfernt wird, legen Sie diese Eigenschaft auf „Absent“ fest.| 
| IncludeAllSubFeature| Legen Sie diese Eigenschaft auf __$true__ fest, um den Status aller erforderlichen Teilfeatures mit dem Status des Features sicherzustellen, das Sie mit der __Name__-Eigenschaft angeben.| 
| LogPath| Gibt den Pfad zu einer Protokolldatei an, in der der Ressourcenanbieter den Vorgang protokollieren soll.| 
| DependsOn| Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Gibt bei Bedarf den Speicherort der Quelldatei an, die für die Installation verwendet werden soll.| 

## <a name="example"></a>Beispiel
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

