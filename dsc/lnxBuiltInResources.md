---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Integrierte PowerShell DSC-Ressourcen für Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Integrierte PowerShell DSC-Ressourcen für Linux

Ressourcen sind Bausteine zum Schreiben eines PowerShell DSC-Skripts. DSC für Linux bietet verschiedene integrierte Funktionen für das Konfigurieren von Ressourcen wie Dateien und Ordnern, Paketen, Umgebungsvariablen sowie Diensten und Prozessen.

## <a name="built-in-resources"></a>Integrierte Ressourcen 

Die folgende Tabelle bietet eine Liste dieser Ressourcen sowie Links zu Themen, in denen diese Ressourcen ausführlich beschrieben werden.

* [nxArchive Ressource](lnxArchiveResource.md): Bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad.
* [nxEnvironment Ressource](lnxEnvironmentResource.md): Verwaltet Umgebungsvariablen auf Zielknoten. 
* [nxFile Ressource](lnxFileResource.md): Verwaltet Linux-Dateien und -Verzeichnisse. 
* [nxFileLine Ressource](lnxFileLineResource.md): Verwaltet einzelne Zeilen in einer Linux-Datei. 
* [nxGroup Ressource](lnxGroupResource.md): Verwaltet lokale Linux-Gruppen. 
* [nxPackage Ressource](lnxPackageResource.md): Verwaltet Pakete auf Linux-Knoten.
* [nxScript Ressource ](lnxScriptResource.md): Führt Skripts auf Zielknoten aus.
* [nxService Ressource](lnxServiceResource.md): Verwaltet Linux-Dienste (Daemons).
* [nxSshAuthorizedKeys Ressource](lnxSshAuthorizedKeysResource.md): Verwaltet öffentliche SSH-Schlüssel für einen Linux-Benutzer. 
* [nxUser Ressource](lnxUserResource.md): Verwaltet lokale Linux-Benutzer. 
  
