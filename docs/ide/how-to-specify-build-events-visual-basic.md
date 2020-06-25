---
title: 'Postupy: určení událostí sestavení (Visual Basic)'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
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
ms.openlocfilehash: 5986576fdf668aba952609dbf241e31d4b3dbf3d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283967"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Postupy: určení událostí sestavení (Visual Basic)

Události sestavení v Visual Basic lze použít ke spouštění skriptů, maker nebo jiných akcí jako součást procesu kompilace. Před kompilací dojde k událostem před sestavením; Po kompilaci dojde k událostem po sestavení.

Události sestavení jsou uvedeny v dialogovém okně **události sestavení** , které jsou k dispozici na stránce **kompilovat** v **Návrháři projektu**.

> [!NOTE]
> Visual Basic Express nepodporuje záznam událostí sestavení. To je podporováno pouze v plném produktu Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak zadat události před sestavením a po sestavení

### <a name="to-specify-a-build-event"></a>Určení události sestavení

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **kompilovat** .

3. Kliknutím na tlačítko **události sestavení** otevřete dialogové okno **události sestavení** .

4. Zadejte argumenty příkazového řádku pro akci před sestavením nebo po sestavení a pak klikněte na **OK**.

    > [!NOTE]
    > Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory *. bat* . Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Pokud událost před sestavením nebo po sestavení není úspěšně dokončena, můžete ukončit sestavení tím, že se akce události ukončí s kódem jiným než nula (0), což označuje úspěšnou akci.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Příklad: jak změnit informace o manifestu pomocí události po sestavení

Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace pomocí příkazu *. exe* s názvem z události po sestavení (soubor *. exe. manifest* v adresáři projektu). Minimální verze operačního systému je číslo se čtyřmi částmi, například 4.10.0.0. K tomu příkaz změní `<dependentOS>` část manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Vytvoření příkazu. exe pro změnu manifestu aplikace

1. Vytvořte konzolovou aplikaci pro příkaz. V nabídce **Soubor** klikněte na položku **Nový** a potom klikněte na položku **Projekt**.

2. V dialogovém okně **Nový projekt** , v uzlu **Visual Basic** vyberte možnost **Windows** a potom šablonu **Konzolová aplikace** . Pojmenujte projekt `ChangeOSVersionVB` .

3. V *Module1. vb*přidejte k ostatním `Imports` příkazům v horní části souboru následující řádek:

   ```vb
   Imports System.Xml
   ```

4. Do tohoto pole přidejte následující kód `Sub Main` :

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

   Příkaz přijímá dva argumenty. První argument je cesta k manifestu aplikace (to je složka, ve které proces sestavení vytváří manifest, obvykle * \<ProjectName> publikování*). Druhým argumentem je nová verze operačního systému.

5. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

6. Zkopírujte soubor *. exe* do adresáře, jako je například *C:\TEMP\ChangeOSVersionVB.exe*.

   Dále vyvolejte tento příkaz v události po sestavení pro změnu manifestu aplikace.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Chcete-li vyvolat událost po sestavení pro změnu manifestu aplikace

1. Vytvořte aplikaci pro Windows pro projekt, který chcete publikovat. V nabídce **Soubor** klikněte na položku **Nový** a potom klikněte na položku **Projekt**.

2. V dialogovém okně **Nový projekt** v uzlu **Visual Basic** vyberte možnost **Desktop Windows** a potom šablonu **model Windows Forms App** . Pojmenujte projekt `VBWinApp` .
3. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

4. V **Návrháři projektu**klikněte na stránku **publikovat** a nastavte **umístění pro publikování** na *C:\Temp*.

5. Publikujte projekt kliknutím na **Publikovat nyní**.

     Soubor manifestu bude sestaven a vložen do souboru *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe. manifest*. Chcete-li zobrazit manifest, klikněte na něj pravým tlačítkem myši a klikněte na příkaz **otevřít**v programu, potom klikněte na **možnost vybrat program v seznamu**a potom klikněte na tlačítko **Poznámkový blok**.

     Vyhledejte v souboru `<osVersionInfo>` element. Například verze může být:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. V **Návrháři projektu**přejděte na kartu **kompilovat** a kliknutím na tlačítko **události sestavení** otevřete dialogové okno **události sestavení** .

7. Do pole **příkazový řádek události po sestavení** zadejte následující příkaz:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Při sestavování projektu tento příkaz změní minimální verzi operačního systému v manifestu aplikace na 5.1.2600.0.

     `$(TargetPath)`Makro vyjadřuje úplnou cestu pro spustitelný soubor, který se vytváří. Proto *$ (TargetPath). manifest* určí manifest aplikace vytvořený v adresáři *bin* . Publikováním se tento manifest zkopíruje do umístění pro publikování, které jste nastavili dříve.

8. Publikujte projekt znovu. Přejděte na stránku **publikovat** a klikněte na **publikovat**.

     Zobrazte manifest znovu. Chcete-li zobrazit manifest, přejděte do adresáře Publish, klikněte pravým tlačítkem myši na soubor a klikněte na příkaz **otevřít** v programu a potom **vyberte požadovaný program v seznamu**a klikněte na tlačítko **Poznámkový blok**.

     Verze by teď měla číst:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Viz také

- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Stránka publikování, Návrhář projektu](../ide/reference/publish-page-project-designer.md)
- [Dialogové okno Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md)
