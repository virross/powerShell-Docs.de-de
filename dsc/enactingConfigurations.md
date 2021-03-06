---
ms.date: 2017-10-16
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Inkraftsetzung von Konfigurationen
ms.openlocfilehash: f9f8889439e43d540b50b68ef13e8e088b8cadd3
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2017
---
# <a name="enacting-configurations"></a>Inkraftsetzung von Konfigurationen

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Es gibt zwei Möglichkeiten, PowerShell DSC-Konfigurationen (Desired State Configuration) anzuwenden: Push- und Pullmodus.

## <a name="push-mode"></a>Pushmodus

![Pushmodus](images/pushModel.png "Funktionsweise des Pushmodus")

Der Pushmodus bezieht sich auf einen Benutzer, der eine Konfiguration durch Aufrufen des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aktiv auf einen Zielknoten anwendet.

Nach dem Erstellen und Kompilieren einer Konfiguration können Sie sie im Pushmodus anwenden, indem Sie das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aufrufen und den Parameter „-Path“ des Cmdlets auf den Pfad festlegen, in dem sich die MOF-Konfigurationsdatei befindet.
Wenn sich die MOF-Konfigurationsdatei z.B. in `C:\DSC\Configurations\localhost.mof` befindet, wenden Sie sie mit dem folgenden Befehl auf den lokalen Computer an: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`.

> __Hinweis__: DSC führt eine Konfiguration standardmäßig als Hintergrundauftrag aus. Um die Konfiguration interaktiv auszuführen, rufen Sie das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) mit dem __-Wait__-Parameter auf.

## <a name="pull-mode"></a>Pullmodus

![Pullmodus](images/pullModel.png "Funktionsweise des Pullmodus")

Im Pullmodus werden Pullclients so konfiguriert, dass sie ihre Konfigurationen des gewünschten Zustands von einem Remotepulldienst erhalten.
Der Pulldienst muss so eingerichtet werden, dass er den DSC-Dienst hostet und mit den Konfigurationen und Ressourcen versehen wird, die von den Pullclients benötigt werden.
Jeder der Pullclients weist ein geplantes Ereignis auf, das für die Konfiguration auf dem Knoten eine regelmäßige Kompatibilitätsprüfung durchführt.
Wenn das Ereignis erstmals ausgelöst wird, sendet der lokale Konfigurations-Manager (LCM) auf dem Pullclient eine Anforderung an den Pulldienst, um die im LCM angegebene Konfiguration abzurufen.
Wenn diese Konfiguration auf dem Pulldienst vorhanden ist und anfängliche Überprüfungen besteht, wird die Konfiguration auf den Pullclient heruntergeladen, auf dem sie vom LCM ausgeführt wird.

Entsprechend den Einstellungen der Eigenschaft **ConfigurationModeFrequencyMins** des LCMs überprüft dieser in regelmäßigen Abständen, ob der Client mit der Konfiguration übereinstimmt.
Entsprechend den Einstellungen der Eigenschaft **RefreshModeFrequency** des LCMs sucht dieser in regelmäßigen Abständen nach aktualisierten Konfigurationen auf dem Pulldienst.
Informationen zum Konfigurieren des LCMs finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md).

Die empfohlene Lösung für das Hosten eines Pulldiensts ist der DSC-Clouddienst, [Azure Automation](https://azure.microsoft.com/en-us/services/automation/).
Diese gehostete Lösung ermöglicht eine grafische Verwaltung, Berichterstellung und zentrale Verwaltung.

Weitere Informationen zum Einrichten eines Pulldiensts unter Windows Server finden Sie unter [Einrichten eines DSC-Webpullservers](pullServer.md).
Beachten Sie jedoch, dass die Funktionen dieser Implementierung eingeschränkt sind und dass einige Integrationsschritte manuell durchgeführt werden müssen.

In den folgenden Themen werden Pulldienst und -clients erläutert:

- [Azure Automation DSC – Übersicht](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Einrichten eines SMB-Pullservers](pullServerSMB.md)
- [Konfigurieren eines Pullclients](pullClientConfigID.md)
