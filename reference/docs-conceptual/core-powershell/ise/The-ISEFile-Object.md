---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das ISEFile-Objekt
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>Das ISEFile-Objekt
  Ein **ISEFile**-Objekt stellt eine Datei in Windows-PowerShell® Integrated Scripting Environment (ISE) dar Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse. In diesem Thema werden die Elementmethoden und -eigenschaften aufgeführt. **$psISE.CurrentFile** und die Dateien in der DateiSammlung auf einer PowerShell-Registerkarte sind Instanzen der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Speichert die Datei auf dem Datenträger.

 **\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll. Der Standardwert lautet **UTF8**.

 **Ausnahmen**
 -   **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(Dateiname, \[saveEncoding\]\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Speichert die Datei mit dem angegebenen Namen und der angegebenen Codierung.

 **Dateiname**: Zeichenfolge – der Name, der zum Speichern der Datei verwendet werden soll.

 **\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll. Der Standardwert lautet **UTF8**.

 **Ausnahmen**
 -   **System.ArgumentNullException**: Der **filename**-Parameter ist NULL.

- **System.ArgumentException**: Der **filename**-Parameter ist leer.

- **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Eigenschaften

### <a name="displayname"></a>DisplayName
  In Windows PowerShell ISE 2.0 und höher unterstützt.

 Die schreibgeschützte Eigenschaft, die die Zeichenfolge mit dem Anzeigenamen dieser Datei abruft. Der Name wird auf der Registerkarte **Datei** oben im Editor angezeigt. Ein Sternchen \(\*\) am Ende des Namens zeigt an, dass die Datei nicht gespeicherte Änderungen enthält.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Editor
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die das für die angegebene Datei verwendete [Editor-Objekt](The-ISEEditor-Object.md) abruft.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Codierung
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die ursprüngliche Dateicodierung abruft. Dies ist ein **System.Text.Encoding**-Objekt.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Zeichenfolge abruft, die den vollständigen Pfad der geöffneten Datei angibt.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte boolesche Eigenschaft, die **$true** zurückgibt, wenn die Datei nach der letzten Änderung gespeichert wurde.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die **$true** zurückgibt, wenn für die Datei nie ein Titel festgelegt wurde.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Weitere Informationen
- [Das ISEFileCollection-Objekt](The-ISEFileCollection-Object.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
