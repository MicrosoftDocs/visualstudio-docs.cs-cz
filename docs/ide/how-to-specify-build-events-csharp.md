---
title: 'Postup: Určení událostí sestavení (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
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
ms.openlocfilehash: 134a5b7cd4bb0ffc9c00a41df12ed196dd2a9212
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115136"
---
# <a name="how-to-specify-build-events-c"></a>Postup: Určení událostí sestavení (C#)

Pomocí událostí sestavení určete příkazy, které se spustí před spuštěním sestavení nebo po dokončení sestavení. Build události spustit pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

Když je projekt vytvořen, události před sestavením jsou přidány do souboru s názvem *PreBuildEvent.bat* a události po sestavení jsou přidány do souboru s názvem *PostBuildEvent.bat*. Pokud chcete zajistit kontrolu chyb, přidejte vlastní příkazy pro kontrolu chyb do kroků sestavení.

## <a name="specify-a-build-event"></a>Určení události sestavení

1. V **Průzkumníku řešení**vyberte projekt, pro který chcete zadat událost sestavení.

2. V nabídce **Project** klepněte na **položku Vlastnosti**.

3. Vyberte kartu **Události sestavení.**

4. V poli **příkazového řádku Události před sestavením** zadejte syntaxi události sestavení.

   > [!NOTE]
   > Události předběžného sestavení se nespustí, pokud je projekt aktuální a neaktivuje se žádné sestavení.

5. V **příkazovém řádku události Po sestavení** zadejte syntaxi události sestavení.

   > [!NOTE]
   > Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory *BAT.* Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

6. V poli **Spustit událost po sestavení** určete, za jakých podmínek má být událost po sestavení spuštěna.

   > [!NOTE]
   > Chcete-li přidat zdlouhavou syntaxi nebo vybrat libovolná makra sestavení z [dialogového okna Příkazového řádku události a po sestavení,](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)zobrazte textové pole klepnutím na tlačítko se třemi tečkami (**...**).

   Syntaxe události sestavení může obsahovat libovolný příkaz platný na příkazovém řádku nebo v souboru *BAT.* Název dávkového souboru by měl `call` předcházet, aby bylo zajištěno, že budou provedeny všechny následné příkazy.

   > [!NOTE]
   > Pokud vaše událost před sestavením nebo po sestavení není úspěšně dokončena, můžete sestavení ukončit ukončením akce události s jiným kódem než nula (0), což znamená úspěšnou akci.

## <a name="example"></a>Příklad

Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace pomocí příkazu *EXE,* který je volán z události post-build (soubor *.exe.manifest* v adresáři projektu). Minimální verze operačního systému je čtyřdílné číslo, například 4.10.0.0. Chcete-li nastavit minimální verzi operačního `<dependentOS>` systému, příkaz změní část manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Vytvoření příkazu EXE pro změnu manifestu aplikace

1. Vytvořte nový projekt **konzolové aplikace** pro příkaz. Název projektu **ChangeOSVersionCS**.

2. V *Program.cs*přidejte následující řádek `using` k ostatním direktivám v horní části souboru:

   ```csharp
   using System.Xml;
   ```

3. V `ChangeOSVersionCS` oboru názvů nahraďte implementaci `Program` třídy následujícím kódem:

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

   Příkaz má dva argumenty: cestu manifestu aplikace (to znamená, že složka, ve které proces sestavení vytvoří manifest, obvykle *Projectname.publish*) a novou verzi operačního systému.

4. Sestavte projekt.

5. Zkopírujte soubor EXE do *adresáře,* například *C:\TEMP\ChangeOSVersionVB.exe*.

Dále vyvolat tento příkaz v post-build události upravit manifest aplikace.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Vyvolání události po sestavení k úpravě manifestu aplikace

1. Vytvořte nový projekt **aplikace Windows Forms App** a pojmenujte jej **CSWinApp**.

2. S vybraným projektem v **Průzkumníku řešení**v nabídce **Projekt** zvolte **Vlastnosti**.

3. V **Návrháři projektu**vyhledejte stránku **Publikování** a nastavte **umístění publikování** na *C:\TEMP*.

4. Publikujte projekt klepnutím na tlačítko **Publikovat nyní**.

   Soubor manifestu je vytvořen a uložen do *souboru C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Chcete-li zobrazit manifest, klepněte pravým tlačítkem myši na soubor, klepněte na příkaz **Otevřít pomocí**, vyberte příkaz Vybrat program **ze seznamu**a potom klepněte na **položku Poznámkový blok**.

   Vyhledejte `<osVersionInfo>` v souboru prvek. Verze může být například:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. V **Návrháři projektu**klikněte na kartu **Události sestavení** a potom klikněte na Upravit **následné sestavení**.

6. Do pole **Posestavení příkazového řádku události** zadejte následující příkaz:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Při vytváření projektu tento příkaz změní minimální verzi operačního systému v manifestu aplikace na 5.1.2600.0.

   Vzhledem `$(TargetPath)` k tomu, že makro vyjadřuje úplnou cestu pro vytvářený spustitelný soubor, `$(TargetPath).manifest` určuje manifest aplikace vytvořený v adresáři *přihrádky.* Publikování zkopíruje tento manifest do umístění publikování, které jste nastavili dříve.

7. Publikujte projekt znovu.

   Verze manifestu by nyní měla číst:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Viz také

- [Stránka Události sestavení, Návrhář projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Dialogové okno Příkazový řádek události před sestavením/Po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Postup: Určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
