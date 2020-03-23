---
title: 'Postup: Určení událostí sestavení (Visual Basic)'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cf9cadc8fbf091fb213926fb25b232d14dc0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115103"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Postup: Určení událostí sestavení (Visual Basic)

Události sestavení v jazyce Visual Basic lze použít ke spuštění skriptů, maker nebo jiných akcí jako součást procesu kompilace. Předsestavení události dojít před kompilací; události po sestavení nastanou po kompilaci.

Události sestavení jsou určeny v dialogovém okně **Události sestavení,** které je k dispozici na stránce **Kompilace** **Návrháře projektu**.

> [!NOTE]
> Visual Basic Express nepodporuje zadávání událostí sestavení. To je podporováno pouze v celém produktu Sady Visual.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak určit události před sestavením a po sestavení

### <a name="to-specify-a-build-event"></a>Určení události sestavení

1. S projektem vybraným v **Průzkumníku řešení**klikněte v nabídce **Projekt** na **příkaz Vlastnosti**.

2. Klikněte na kartu **Kompilace.**

3. Klepnutím na tlačítko **Sestavy událostí** otevřete dialogové okno **Události sestavení.**

4. Zadejte argumenty příkazového řádku pro akci před sestavením nebo po sestavení a klepněte na tlačítko **OK**.

    > [!NOTE]
    > Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory *BAT.* Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Pokud vaše událost před sestavením nebo po sestavení není úspěšně dokončena, můžete sestavení ukončit ukončením akce události s jiným kódem než nula (0), což znamená úspěšnou akci.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Příklad: Jak změnit informace o manifestu pomocí události po sestavení

Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace pomocí příkazu *EXE* volaném z události post-build (soubor *u.exe.manifest* v adresáři projektu). Minimální verze operačního systému je čtyřdílné číslo, například 4.10.0.0. Chcete-li to provést, `<dependentOS>` příkaz změní část manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Vytvoření příkazu EXE pro změnu manifestu aplikace

1. Vytvořte konzolovou aplikaci pro příkaz. V nabídce **Soubor** klikněte na položku **Nový** a potom klikněte na položku **Projekt**.

2. V dialogovém okně **Nový projekt** vyberte v uzlu **Visual Basic** systém **Windows** a potom šablonu **konzolové aplikace.** Pojmenujte `ChangeOSVersionVB`projekt .

3. V *modulu 1.vb*přidejte následující `Imports` řádek k ostatním příkazům v horní části souboru:

   ```vb
   Imports System.Xml
   ```

4. Do tohoto textu `Sub Main`přidejte následující kód:

   ```vb
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

   Příkaz trvá dva argumenty. Prvním argumentem je cesta k manifestu aplikace (to znamená složka, ve které proces sestavení vytvoří manifest, obvykle * \<Název_projektu>.publish).* Druhým argumentem je nová verze operačního systému.

5. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

6. Zkopírujte soubor EXE do *adresáře,* například *C:\TEMP\ChangeOSVersionVB.exe*.

   Dále vyvolat tento příkaz v post-build události změnit manifest aplikace.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Vyvolání události po sestavení ke změně manifestu aplikace

1. Vytvořte aplikaci systému Windows pro projekt, který má být publikován. V nabídce **Soubor** klikněte na položku **Nový** a potom klikněte na položku **Projekt**.

2. V dialogovém okně **Nový projekt** vyberte v uzlu **Visual Basic** plochu **windows** a potom šablonu Aplikace **Windows Forms.** Pojmenujte `VBWinApp`projekt .
3. S vybraným projektem v **Průzkumníku řešení**klikněte v nabídce **Projekt** na **příkaz Vlastnosti**.

4. V **Návrháři projektu**přejděte na stránku **Publikovat** a nastavte **umístění publikování** na *C:\TEMP*.

5. Publikujte projekt klepnutím na tlačítko **Publikovat nyní**.

     Soubor manifestu bude vytvořen a vložen do *souboru C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Chcete-li zobrazit manifest, klepněte pravým tlačítkem myši na soubor a klepněte na příkaz **Otevřít pomocí**, potom klepněte na příkaz Vybrat program **ze seznamu**a potom klepněte na **položku Poznámkový blok**.

     Vyhledejte `<osVersionInfo>` v souboru prvek. Verze může být například:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. V **Návrháři projektu**přejděte na kartu **Kompilace** a klepnutím na tlačítko **Události sestavení** otevřete dialogové okno **Události sestavení.**

7. Do pole **Posestavení příkazového řádku události** zadejte následující příkaz:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Při vytváření projektu tento příkaz změní minimální verzi operačního systému v manifestu aplikace na 5.1.2600.0.

     Makro `$(TargetPath)` vyjadřuje úplnou cestu pro vytvářený spustitelný soubor. Proto *$(TargetPath).manifest* bude určovat manifest aplikace vytvořený v adresáři *bin.* Publikování zkopíruje tento manifest do umístění publikování, které jste nastavili dříve.

8. Publikujte projekt znovu. Přejděte na stránku **Publikovat** a klepněte na **tlačítko Publikovat nyní**.

     Znovu zobrazit manifest. Chcete-li zobrazit manifest, přejděte do adresáře publikování, klepněte pravým tlačítkem myši na soubor a klepněte na příkaz **Otevřít pomocí** souboru a potom **vyberte program ze seznamu**a potom klepněte na **položku Poznámkový blok**.

     Verze by nyní měla číst:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Viz také

- [Stránka kompilace, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Stránka Publikování, Návrhář projektu](../ide/reference/publish-page-project-designer.md)
- [Dialogové okno Příkazový řádek události před sestavením/Po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Postup: Určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md)
