---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Arbeiten mit Druckern
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a>Arbeiten mit Druckern
Sie können Windows PowerShell zum Verwalten von Druckern mit WMI und dem COM-Objekt „WScript.Network“ vom WSH verwenden. Wir werden eine Kombination beider Tools verwenden, um bestimmte Aufgaben zu veranschaulichen.

### <a name="listing-printer-connections"></a>Auflisten von Druckerverbindungen
Die einfachste Möglichkeit, die auf einem Computer installierten Drucker aufzulisten, ist die Verwendung der WMI-Klasse **Win32_Printer**:

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

Sie können die Drucker auch mit dem COM-Objekt **WScript.Network** auflisten, das normalerweise in WSH-Skripts verwendet wird:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Da dieser Befehl eine einfache Zeichenfolgenauflistung von Portnamen und Druckergerätenamen ohne unterscheidende Bezeichnungen zurückgibt, ist die Ausgabe nicht leicht zu interpretieren.

### <a name="adding-a-network-printer"></a>Hinzufügen eines Netzwerkdruckers
Verwenden Sie zum Hinzufügen eines neuen Netzwerkdruckers **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Festlegen eines Standarddruckers
Um mithilfe von WMI den Standarddrucker festzulegen, suchen Sie den Drucker in der **Win32_Printer**-Sammlung, und rufen Sie dann die Methode **SetDefaultPrinter** auf:

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** ist etwas einfacher zu verwenden, da es eine **SetDefaultPrinter**-Methode besitzt, die nur den Druckernamen als Argument akzeptiert:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Entfernen einer Druckerverbindung
Um eine Druckerverbindung zu entfernen, verwenden Sie die Methode **WScript.Network RemovePrinterConnection**:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

