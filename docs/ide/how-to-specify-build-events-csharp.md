---
title: 'Postupy: určení událostí sestavení (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e1a3083b59ad0cec727f753395768a214ff571b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283993"
---
# <a name="how-to-specify-build-events-c"></a>Postupy: určení událostí sestavení (C#)

Pomocí událostí sestavení můžete zadat příkazy, které se spustí před spuštěním sestavení nebo po dokončení sestavení. Události sestavení se spustí pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

Když je projekt sestaven, události před sestavením jsou přidány do souboru s názvem *PreBuildEvent.bat* a události po sestavení jsou přidány do souboru s názvem *PostBuildEvent.bat*. Pokud chcete zajistit kontrolu chyb, přidejte do kroků sestavení vlastní příkazy pro kontrolu chyb.

## <a name="specify-a-build-event"></a>Zadat událost sestavení

1. V **Průzkumník řešení**vyberte projekt, pro který chcete zadat událost sestavení.

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

3. Vyberte kartu **události sestavení** .

4. V poli **příkazový řádek události před sestavením** zadejte syntaxi události sestavení.

   > [!NOTE]
   > Události před sestavením se nespustí, pokud je projekt aktuální a není spuštěno žádné sestavení.

5. V poli **příkazový řádek události po sestavení** zadejte syntaxi události sestavení.

   > [!NOTE]
   > Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory *. bat* . Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

6. V poli **Spustit událost po sestavení** určete, za jakých podmínek se má spustit událost po sestavení.

   > [!NOTE]
   > Chcete-li přidat syntaxi s délkou, nebo vybrat makra sestavení z [dialogového okna Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), klikněte na tlačítko se třemi tečkami (**...**) a zobrazte textové pole.

   Syntaxe události sestavení může obsahovat jakýkoli příkaz, který je platný na příkazovém řádku nebo v souboru *. bat* . Název dávkového souboru by měl předcházet `call` , aby bylo zajištěno, že budou provedeny všechny následné příkazy.

   > [!NOTE]
   > Pokud událost před sestavením nebo po sestavení není úspěšně dokončena, můžete ukončit sestavení tím, že se akce události ukončí s kódem jiným než nula (0), což označuje úspěšnou akci.

## <a name="example"></a>Příklad

Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace pomocí příkazu *. exe* , který je volán z události po sestavení (soubor *. exe. manifest* v adresáři projektu). Minimální verze operačního systému je číslo se čtyřmi částmi, například 4.10.0.0. Pro nastavení minimální verze operačního systému příkaz změní `<dependentOS>` část manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Vytvoření příkazu. exe pro změnu manifestu aplikace

1. Vytvořte nový projekt **konzolové aplikace** pro příkaz. Pojmenujte projekt **ChangeOSVersionCS**.

2. V *program.cs*přidejte následující řádek do dalších `using` direktiv v horní části souboru:

   ```csharp
   using System.Xml;
   ```

3. V `ChangeOSVersionCS` oboru názvů nahraďte `Program` implementaci třídy následujícím kódem:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

   Příkaz přijímá dva argumenty: cestu manifestu aplikace (tj. složka, ve které proces sestavení vytváří manifest, obvykle *ProjectName. Publish*) a novou verzi operačního systému.

4. Sestavte projekt.

5. Zkopírujte soubor *. exe* do adresáře, jako je například *C:\TEMP\ChangeOSVersionVB.exe*.

Dále vyvolejte tento příkaz v události po sestavení pro úpravu manifestu aplikace.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Vyvolat událost po sestavení pro úpravu manifestu aplikace

1. Vytvořte nový projekt **aplikace model Windows Forms** a pojmenujte ho **CSWinApp**.

2. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** vyberte **vlastnosti**.

3. V **Návrháři projektu**Najděte stránku **publikování** a nastavte **umístění pro publikování** na *C:\Temp*.

4. Publikujte projekt kliknutím na **Publikovat nyní**.

   Soubor manifestu je sestaven a uložen do souboru *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe. manifest*. Chcete-li zobrazit manifest, klikněte pravým tlačítkem myši na soubor, klikněte na možnost **otevřít**v aplikaci, vyberte **možnost vybrat program v seznamu**a pak klikněte na tlačítko **Poznámkový blok**.

   Vyhledejte v souboru `<osVersionInfo>` element. Například verze může být:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. Zpět v **Návrháři projektu**klikněte na kartu **události sestavení** a pak klikněte na **Upravit po sestavení**.

6. Do pole **příkazový řádek události po sestavení** zadejte následující příkaz:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Při sestavování projektu tento příkaz změní minimální verzi operačního systému v manifestu aplikace na 5.1.2600.0.

   Vzhledem k tomu, že `$(TargetPath)` makro vyjadřuje úplnou cestu pro vytvářený spustitelný soubor, `$(TargetPath).manifest` určí manifest aplikace vytvořený v adresáři *bin* . Publikování zkopíruje tento manifest do umístění pro publikování, které jste nastavili dříve.

7. Publikujte projekt znovu.

   Verze manifestu by teď měla číst:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Viz také

- [Stránka události sestavení, Návrhář projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Dialogové okno Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
