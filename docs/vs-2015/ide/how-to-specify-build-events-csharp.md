---
title: 'Postupy: určení událostí sestavení (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41d3ef0efd4c9eb8eab16bd12cc79f8df1449d65
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670691"
---
# <a name="how-to-specify-build-events-c"></a>Postupy: Specifikace událostí sestavení (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí událostí sestavení můžete zadat příkazy, které se spustí před spuštěním sestavení nebo po dokončení sestavení. Události sestavení jsou spouštěny pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

 Při sestavení projektu jsou události před sestavením přidány do souboru s názvem PreBuildEvent. bat a události po sestavení jsou přidány do souboru s názvem PostBuildEvent. bat. Pokud chcete zajistit kontrolu chyb, přidejte do kroků sestavení vlastní příkazy pro kontrolu chyb.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak zadat události před sestavením a po sestavení

#### <a name="to-specify-a-build-event"></a>Určení události sestavení

1. V **Průzkumník řešení**vyberte projekt, pro který chcete zadat událost sestavení.

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

3. Vyberte kartu **události sestavení** .

4. V poli **příkazový řádek události před sestavením** zadejte syntaxi události sestavení.

    > [!NOTE]
    > Události před sestavením se nespustí, pokud je projekt aktuální a není spuštěno žádné sestavení.

5. V poli **příkazový řádek události po sestavení** zadejte syntaxi události sestavení.

    > [!NOTE]
    > Přidejte příkaz `call` před všechny příkazy po sestavení, které spouštějí soubory. bat. Například `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

6. V poli **Spustit událost po sestavení** určete, za jakých podmínek se má spustit událost po sestavení.

    > [!NOTE]
    > Chcete-li přidat syntaxi s délkou, nebo vybrat makra sestavení z [dialogového okna Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), klikněte na tlačítko se třemi tečkami ( **...** ) a zobrazte textové pole.

     Syntaxe události sestavení může obsahovat jakýkoli příkaz, který je platný na příkazovém řádku nebo v souboru. bat. Název dávkového souboru by měl předcházet `call`, aby bylo zajištěno, že budou provedeny všechny následné příkazy.

     **Poznámka:** Pokud událost před sestavením nebo po sestavení není úspěšně dokončena, můžete ukončit sestavení tím, že se akce události ukončí s kódem jiným než nula (0), což označuje úspěšnou akci.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Příklad: jak změnit informace o manifestu pomocí události po sestavení
 Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace pomocí příkazu. exe, který je volán z události po sestavení (soubor. exe. manifest v adresáři projektu). Minimální verze operačního systému je číslo se čtyřmi částmi, například 4.10.0.0. K tomu příkaz změní část `<dependentOS>` manifestu:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Vytvoření příkazu. exe pro změnu manifestu aplikace

1. Vytvořte konzolovou aplikaci pro příkaz. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **vizuál C#** , klikněte na možnost **Windows**a potom klikněte na šablonu **Konzolová aplikace** . Pojmenujte projekt `ChangeOSVersionCS`.

3. V Program.cs přidejte následující řádek do dalších příkazů `using` v horní části souboru:

   ```
   using System.Xml;
   ```

4. V oboru názvů `ChangeOSVersionCS` nahraďte implementaci `Program` třídy následujícím kódem:

   ```
   class Program
   {
      /// <summary>
      /// This function will set the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest).
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

    Příkaz přijímá dva argumenty: cestu manifestu aplikace (tj. složka, ve které proces sestavení vytváří manifest, obvykle ProjectName. Publish) a novou verzi operačního systému.

5. Sestavte projekt. V nabídce **sestavení** klikněte na **Sestavit řešení**.

6. Zkopírujte soubor. exe do adresáře, jako je například `C:\TEMP\ChangeOSVersionVB.exe`.

   Dále vyvolejte tento příkaz v události po sestavení pro úpravu manifestu aplikace.

#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Chcete-li vyvolat událost po sestavení pro úpravu manifestu aplikace

1. Vytvořte aplikaci pro Windows pro projekt, který chcete publikovat. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **vizuál C#** , klikněte na možnost **Windows**a potom klikněte na šablonu **aplikace model Windows Forms** . Pojmenujte projekt `CSWinApp`.

3. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

4. V Návrháři projektu Najděte stránku **publikování** a nastavte **umístění publikování** na `C:\TEMP\`.

5. Publikujte projekt kliknutím na **Publikovat nyní**.

     Soubor manifestu bude sestaven a umístěn do `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Chcete-li zobrazit manifest, klikněte pravým tlačítkem myši na soubor, klikněte na možnost **otevřít**v aplikaci, vyberte **možnost vybrat program v seznamu**a pak klikněte na tlačítko **Poznámkový blok**.

     V souboru vyhledejte `<osVersionInfo>` element. Například verze může být:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. V Návrháři projektu klikněte na kartu **události sestavení** a klikněte na tlačítko **Upravit po sestavení** .

7. Do pole **příkazový řádek události po sestavení** zadejte následující příkaz:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Při sestavování projektu tento příkaz změní minimální verzi operačního systému v manifestu aplikace na 5.1.2600.0.

     Vzhledem k tomu, že makro `$(TargetPath)` vyjadřuje úplnou cestu pro vytvářený spustitelný soubor, v souboru `$(TargetPath)`. manifest se určí manifest aplikace vytvořený v adresáři bin. Publikováním se tento manifest zkopíruje do umístění pro publikování, které jste nastavili dříve.

8. Publikujte projekt znovu. Přejděte na stránku **publikovat** a klikněte na **publikovat**.

     Zobrazte manifest znovu. Chcete-li zobrazit manifest, otevřete adresář pro publikování, klikněte pravým tlačítkem myši na soubor, klikněte na možnost **otevřít**v aplikaci, vyberte **možnost vybrat program v seznamu**a klikněte na tlačítko **Poznámkový blok**.

     Verze by teď měla číst:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Viz také
 [Stránka události sestavení, Návrhář projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md) [dialogové okno Příkazový řádek události před sestavením/po sestavení –](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [Postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md) [kompilace a sestavování](../ide/compiling-and-building-in-visual-studio.md)
