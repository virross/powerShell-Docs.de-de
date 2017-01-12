---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: JEA-Voraussetzungen
ms.technology: powershell
ms.openlocfilehash: c709b3692705db327245e4e1b3fde800ac7d57a9
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="prerequisites"></a>Voraussetzungen

> Gilt für: Windows PowerShell 5.0

„Just Enough Administration“ ist ein in Windows PowerShell 5.0 und höher enthaltenes Feature.
Dieses Thema beschreibt die Voraussetzungen, die erfüllt sein müssen, um JEA verwenden zu können.

## <a name="install-jea"></a>Installieren von JEA
JEA ist in Windows PowerShell 5.0 und höher verfügbar. Wenn Sie jedoch die vollständige Funktionalität nutzen möchten, empfehlen wir Ihnen die Installation der neuesten Version von PowerShell für Ihr Betriebssystem.
Die folgende Tabelle beschreibt die Verfügbarkeit von JEA für jedes unterstützte Betriebssystem.

Betriebssystem          | JEA-Verfügbarkeit
--------------------------|------------------------------------------------------
Windows Server 2016       | Vorinstalliert
Windows Server 2012 R2    | Vollständige Funktionalität mit WMF 5.1
Windows Server 2012       | Vollständige Funktionalität mit WMF 5.1
Windows Server 2008 R2    | Vollständige Funktionalität mit WMF 5.1
Windows 10 1607           | Vorinstalliert
Windows 10 1603, 1511     | Vorinstalliert, mit eingeschränkter Funktionalität<sup>1</sup>
Windows 10 1507           | Nicht verfügbar
Windows 8, 8.1            | Vollständige Funktionalität mit WMF 5.1
Windows 7                 | Eingeschränkte Funktionalität<sup>2</sup> mit WMF 5.1

<sup>1</sup> Die folgenden JEA-Features werden von den Windows 10-Versionen 1511 und 1603 nicht unterstützt: Ausführen als gruppenverwaltetes Dienstkonto, bedingte Zugriffsregeln in Sitzungskonfigurationen, Benutzerlaufwerk und Gewähren von Zugriff auf lokale Benutzerkonten.
Aktualisieren Sie Windows auf Version 1607 (Anniversary Update) oder höher, um Unterstützung für diese Features zu erhalten.

<sup>2</sup> JEA kann nicht für die Verwendung von virtuellen Konten unter Windows 7 konfiguriert werden.

### <a name="check-which-version-of-powershell-is-installed"></a>Überprüfen der installierten Version von PowerShell
Überprüfen Sie die `$PSVersionTable`-Variable in einer Windows PowerShell-Aufforderung, um festzustellen, welche PowerShell-Version auf Ihrem System installiert ist.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Sie können JEA verwenden, wenn die *Hauptversion* mindestens **5** ist.
Wir empfehlen Ihnen, soweit möglich, ein Upgrade auf die PowerShell-Version **5.1** durchzuführen, um sich optimale Ergebnisse und Zugriff auf die neuesten Features zu sichern.

### <a name="install-windows-management-framework"></a>Installieren von Windows Management Framework
Wenn Sie eine ältere Version von PowerShell ausführen, müssen Sie Ihr System mit dem aktuellen Update von Windows Management Framework (WMF) aktualisieren.
Updatepakete und einen Link zu den neuesten Anmerkungen zur WMF-Version finden Sie im [Download Center](https://aka.ms/WMF5).

Es wird dringend empfohlen, vor dem Upgrade aller Server die Kompatibilität Ihrer Workload mit WMF zu testen.

Windows 10-Benutzer sollten die neuesten Funktionsupdates zum Abrufen der aktuellen Version von Windows PowerShell installieren.

## <a name="enable-powershell-remoting"></a>Aktivieren von PowerShell-Remoting
PowerShell-Remoting stellt die Grundlage für JEA dar.
Daher sollten Sie sicherstellen, dass PowerShell-Remoting aktiviert ist und auf Ihrem System [ordnungsgemäß abgesichert](https://msdn.microsoft.com/en-us/powershell/scripting/setup/winrmsecurity) ist, bevor Sie JEA verwenden können.

PowerShell-Remoting ist unter Windows Server 2012, 2012 R2 und 2016 standardmäßig aktiviert.
Sie können PowerShell-Remoting aktivieren, indem Sie den folgenden Befehl in einem PowerShell-Fenster mit erhöhten Rechten ausführen.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Aktivieren der PowerShell-Modul- und Skriptblockprotokollierung (optional)
Die folgenden Schritte aktivieren die Protokollierung für alle PowerShell-Aktionen in Ihrem System.
Für JEA ist die PowerShell-Modulprotokollierung nicht erforderlich. Es wird jedoch dringend empfohlen, dass Sie dieses Feature aktivieren, um sicherzustellen, dass von Benutzern ausgeführte Befehle an einem zentralen Ort protokolliert werden.

Sie können die Richtlinien für die PowerShell-Modulprotokollierung mithilfe von Gruppenrichtlinien konfigurieren.

1. Öffnen Sie den Editor für lokale Gruppenrichtlinien auf einer Arbeitsstation oder ein Gruppenrichtlinienobjekt in der Gruppenrichtlinien-Verwaltungskonsole auf einem Active Directory-Domänencontroller.
2. Navigieren Sie zu **Computerkonfiguration\\Administrative Vorlagen\\Windows-Komponenten\\Windows PowerShell**.
3. Doppelklicken Sie auf **Modulprotokollierung aktivieren**.
4. Klicken Sie auf **Aktiviert**.
5. Klicken Sie im Abschnitt „Optionen“ neben den Modulnamen auf **Anzeigen** 
6. Geben Sie „**\***“ in das Popupfenster ein. So wird PowerShell angewiesen, Befehle aus allen Modulen zu protokollieren.
7. Klicken Sie auf **OK**, um die Richtlinie festzulegen.
8. Doppelklicken Sie anschließend auf **Protokollierung von PowerShell-Skriptblöcken aktivieren**.
9. Klicken Sie auf **Aktiviert**.
10. Klicken Sie auf „**OK“, um die Richtlinie festzulegen.
11. (Nur auf der Domäne zugehörige Computer:) Führen Sie **gpupdate** aus, oder warten Sie, bis die Gruppenrichtlinie die aktualisierte Richtlinie verarbeitet hat und diese Einstellungen anwendet.

Sie können über eine Gruppenrichtlinie auch die systemweite PowerShell-Aufzeichnung aktivieren.

## <a name="next-steps"></a>Nächste Schritte

- [Create a role capability file (Erstellen einer Rollenfunktionsdatei)](role-capabilities.md)
- [Create a session configuration file (Erstellen einer Sitzungskonfigurationsdatei)](session-configurations.md)

## <a name="see-also"></a>Siehe auch
- [Sicherheitsaspekte von PowerShell-Remoting](https://msdn.microsoft.com/en-us/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)