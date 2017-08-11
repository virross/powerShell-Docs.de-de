---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Starten der 32-Bit-Version von Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starten der 32-Bit-Version von Windows PowerShell
Bei der Installation von Windows PowerShell auf einem 64-Bit-Computer wird **Windows PowerShell (x86)**, eine 32-Bit-Version von Windows PowerShell, zusätzlich zur 64-Bit-Version installiert. Wenn Sie Windows PowerShell ausführen, wird standardmäßig die 64-Bit-Version ausgeführt.

Es kann jedoch möglicherweise erforderlich sein, **Windows PowerShell (x86)** auszuführen, z.B. wenn Sie ein Modul verwenden, das die 32-Bit-Version verlangt, oder Sie eine Remoteverbindung mit einem 32-Bit-Computer herstellen.

Wählen Sie eines der folgenden Verfahren, um eine 32-Bit-Version von Windows PowerShell zu starten.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

-   Geben Sie im**** Startbildschirm **Windows PowerShell (x86)** ein. Klicken Sie auf die Kachel **Windows PowerShell x86**.

-   Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.

-   Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.

-   Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

-   Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.

-   Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.

-   Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.

-   Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

-   Geben Sie im**** Startbildschirm **Windows PowerShell (x86)** ein. Klicken Sie auf die Kachel **Windows PowerShell x86**.

-   Falls Sie die [Remoteserver-Verwaltungstools](http://go.microsoft.com/fwlink/?LinkID=304145) für Windows 8.1 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen. Wählen Sie **Windows PowerShell (x86)** aus.

-   Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
   
-   Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

-   Bewegen Sie auf dem Bildschirm **Start** den Cursor in die rechte obere Ecke, klicken Sie auf **Einstellungen**, dann auf **Kacheln**, und bewegen Sie den Schieberegler **Verwaltungstools anzeigen** auf „Ja“. Geben Sie dann **PowerShell** ein, und klicken Sie auf **Windows PowerShell (x86)**.

-   Falls Sie die [Remoteserver-Verwaltungstools](http://www.microsoft.com/download/details.aspx?id=28972) für Windows 8 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen. Wählen Sie **Windows PowerShell (x86)** aus.

-   Geben Sie auf dem Bildschirm **Start** oder dem Desktop **PowerShell (x86)** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.

-   Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
