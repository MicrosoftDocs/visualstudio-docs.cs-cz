---
title: 'Postupy: určení sestavení události (Visual Basic)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24eb6d7637f949abf60eeb2d0659fac1bfa1cae7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831730"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Postupy: určení sestavení události (Visual Basic)

Událostí sestavení v jazyce Visual Basic můžete použít ke spouštění skriptů, maker nebo jiných akcí jako součást procesu kompilace. Před kompilací; dojde k události před sestavením Po kompilaci dojde k události po sestavení.

Sestavení události jsou uvedeny v **události sestavení** dialogovém okně k dispozici **kompilaci** stránku **Návrháře projektu**.

> [!NOTE]
> Visual Basic Express nepodporuje zadání událostí sestavení. To je podporováno pouze v plné verze produktu Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Určení události před sestavením a po sestavení

### <a name="to-specify-a-build-event"></a>K určení událostí sestavení

1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2.  Klikněte na tlačítko **kompilaci** kartu.

3.  Klikněte na tlačítko **události sestavení** tlačítko Otevřít **události sestavení** dialogové okno.

4.  Zadejte argumenty příkazového řádku pro vaši akci před sestavením nebo po sestavení a pak klikněte na tlačítko **OK**.

    > [!NOTE]
    > Přidat `call` příkaz před vše post-build příkazy, které spouštějí *.bat* soubory. Například `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Pokud události před sestavením nebo po sestavení úspěšně nedokončí, můžete ukončit sestavení tak, že vaše akce události ukončení s kódem než nula (0), který označuje úspěšné akce.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Příklad: Jak změnit informace o manifestu pomocí událost po sestavení

Následující postup ukazuje, jak nastavit minimální verzi operačního systému v aplikaci manifestu pomocí *.exe* příkaz volat z události po sestavení ( *. exe.manifest* soubor v projektu adresář). Minimální verzi operačního systému je složené ze čtyř částí čísla, jako je například 4.10.0.0. K tomu příkaz změní `<dependentOS>` manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Chcete-li vytvořit příkaz .exe změna manifestu aplikace

1. Vytvořte konzolovou aplikaci pro příkaz. Z **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

2. V **nový projekt** v dialogu **jazyka Visual Basic** uzlu, vyberte **Windows** a pak **konzolovou aplikaci** šablony. Pojmenujte projekt `ChangeOSVersionVB`.

3. V *Module1.vb*, přidejte následující řádek do jiné `Imports` příkazů v horní části souboru:

   ```vb
   Imports System.Xml
   ```

4. Přidejte následující kód do `Sub Main`:

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

   Příkaz přebírá dva argumenty. První argument je cesta k manifestu aplikace (to znamená, složka, ve které proces sestavení vytvoří manifest, obvykle  *<Projectname>.publish*). Druhý argument je nová verze operačního systému.

5. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

6. Kopírovat *.exe* soubor do adresáře například *C:\TEMP\ChangeOSVersionVB.exe*.

   V dalším kroku vyvolání tohoto příkazu v události po sestavení změňte manifest aplikace.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Chcete-li vyvolat událost po sestavení, chcete-li změnit manifest aplikace

1.  Vytvoření aplikace Windows pro projekt, který má být publikován. Z **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

2.  V **nový projekt** v dialogu **jazyka Visual Basic** uzlu, vyberte **Windows Desktop** a pak **aplikace Windows Forms** šablony. Pojmenujte projekt `VBWinApp`.
3.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

4.  V **Návrháře projektu**, přejděte **publikovat** stránku a nastavit **umístění pro publikování** k *C:\TEMP*.

5.  Publikování projektu kliknutím **publikovat**.

     Soubor manifestu bude sestaven a vložit *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Manifest, klikněte pravým tlačítkem na soubor a pak kliknete na **otevřít v programu**, klikněte na **ze seznamu vyberte program**a potom klikněte na tlačítko **Poznámkový blok**.

     Hledání v souboru `<osVersionInfo>` elementu. Například může být verze:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6.  V **Návrháře projektu**, přejděte na stránku **kompilaci** kartě a klikněte na tlačítko **události sestavení** tlačítko Otevřít **události sestavení** dialogové okno.

7.  V **příkazový řádek události po sestavení** zadejte následující příkaz:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Při sestavování projektu se tento příkaz změní 5.1.2600.0 minimální verzi operačního systému v manifestu aplikace.

     `$(TargetPath)` – Makro vyjadřuje úplnou cestu ke spustitelnému souboru, který vytváří. Proto *.manifest $(TargetPath)* určí manifestem aplikace vytvořeným v *bin* adresáře. Publikování zkopíruje tento manifest na umístění pro publikování, který jste nastavili dříve.

8.  Znovu publikujte projekt. Přejděte **publikovat** stránky a klikněte na tlačítko **publikovat**.

     Zobrazte manifest znovu. Chcete-li zobrazit manifest, přejděte do adresáře publikovat, klikněte pravým tlačítkem na soubor a klikněte na tlačítko **otevřít v programu** a potom **ze seznamu vyberte program**a potom klikněte na **Poznámkový blok**.

     Verze by nyní mělo:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Viz také:

- [Stránka kompilovat, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Publikovat stranu, Návrhář projektu](../ide/reference/publish-page-project-designer.md)
- [Dialogové okno Příkazový řádek události před sestavením události/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md)