---
title: 'Postupy: určení událostí sestavení (C#) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b645d51594cbb507ea0e6bb27a00eea21e73b7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872015"
---
# <a name="how-to-specify-build-events-c"></a>Postupy: Specifikace událostí sestavení (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití událostí sestavení zadat příkazy, na kterých běží před začátkem sestavení nebo po dokončení sestavení. Události sestavení jsou spouštěny pouze v případě, že se sestavení úspěšně dosáhne těchto bodů v procesu sestavení.  
  
 Při vytváření projektu, události před sestavením jsou přidány do souboru s názvem PreBuildEvent.bat a události po sestavení jsou přidány do souboru s názvem PostBuildEvent.bat. Pokud chcete zajistit kontrolu chyb, přidejte vlastní příkazy kontroly chyb do kroků sestavení.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>Určení události před sestavením a po sestavení  
  
#### <a name="to-specify-a-build-event"></a>K určení událostí sestavení  
  
1.  V **Průzkumníka řešení**, vyberte projekt, pro které chcete k určení událostí sestavení.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
3.  Vyberte **události sestavení** kartu.  
  
4.  V **příkazový řádek události před sestavením** zadejte syntaxe události sestavení.  
  
    > [!NOTE]
    >  Události před sestavením nebudou spuštěny, pokud je aktuální projekt a není aktivováno žádné sestavení.  
  
5.  V **příkazový řádek události po sestavení** zadejte syntaxe události sestavení.  
  
    > [!NOTE]
    >  Přidat `call` než vše post-build příkazy, které spouštějí soubory .bat. Například `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  V **spustit událost po sestavení** zadejte za jakých podmínek spustit událost po sestavení.  
  
    > [!NOTE]
    >  Přidejte zdlouhavé syntaxi, nebo vyberte některý makra ze sestavení [pre-build Event/po sestavení příkazového řádku dialogové okno události](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), klikněte na tlačítko se třemi tečkami (**...** ) k zobrazení do textového pole.  
  
     Syntaxe událost sestavení může obsahovat jakýkoli příkaz, který je platný, na příkazovém řádku nebo v souboru bat. Název souboru služby batch by měl předcházet `call` zajistit, že jsou provedeny všechny následné příkazy.  
  
     **Poznámka:** Pokud události před sestavením nebo po sestavení úspěšně nedokončí, můžete ukončit sestavení tak, že vaše akce události ukončení s kódem než nula (0), který označuje úspěšné akce.  
  
## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Příklad: Jak změnit informace o manifestu v události po sestavení  
 Následující postup ukazuje, jak nastavit minimální verzi operačního systému v manifestu aplikace s použitím příkazu k .exe, která je volána z události po sestavení (. exe.manifest soubor v adresáři projektu). Minimální verzi operačního systému je složené ze čtyř částí čísla, jako je například 4.10.0.0. K tomu příkaz změní `<dependentOS>` manifestu:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Chcete-li vytvořit příkaz .exe změna manifestu aplikace  
  
1. Vytvořte konzolovou aplikaci pro příkaz. Z **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2. V **nový projekt** dialogového okna rozbalte **Visual C#**, klikněte na tlačítko **Windows**a potom klikněte na tlačítko **konzolovou aplikaci** šablony. Pojmenujte projekt `ChangeOSVersionCS`.  
  
3. V souboru Program.cs přidejte následující řádek do jiné `using` příkazů v horní části souboru:  
  
   ```  
   using System.Xml;  
   ```  
  
4. V `ChangeOSVersionCS` obor názvů, nahraďte `Program` implementace třídy následujícím kódem:  
  
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
  
    Příkaz přebírá dva argumenty: cesta k manifestu aplikace (to znamená, složka, ve které proces sestavení vytvoří manifest, obvykle Projectname.publish) a nová verze operačního systému.  
  
5. Sestavte projekt. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
6. Kopírování souboru .exe do jiného adresáře, jako `C:\TEMP\ChangeOSVersionVB.exe`.  
  
   V dalším kroku vyvolání tohoto příkazu v události po sestavení upravit manifest aplikace.  
  
#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Chcete-li vyvolat událost po sestavení upravit manifest aplikace  
  
1.  Vytvoření aplikace Windows pro projekt, který má být publikován. Z **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#**, klikněte na tlačítko **Windows**a potom klikněte na tlačítko **formulářová aplikace Windows** šablony. Pojmenujte projekt `CSWinApp`.  
  
3.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
4.  V Návrháři projektu, vyhledejte **publikovat** stránku a nastavit **umístění pro publikování** k `C:\TEMP\`.  
  
5.  Publikování projektu kliknutím **publikovat**.  
  
     Soubor manifestu bude sestaven a vložit `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Pokud chcete zobrazit manifest, klikněte pravým tlačítkem na soubor, klikněte na tlačítko **otevřít v programu**vyberte **ze seznamu vyberte program**a potom klikněte na tlačítko **Poznámkový blok**.  
  
     Hledání v souboru `<osVersionInfo>` elementu. Například může být verze:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  V Návrháři projektu, klikněte na tlačítko **události sestavení** kartě a klikněte na tlačítko **upravit POST-Build** tlačítko.  
  
7.  V **příkazový řádek události po sestavení** pole, zadejte následující příkaz:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Při sestavování projektu se tento příkaz změní 5.1.2600.0 minimální verzi operačního systému v manifestu aplikace.  
  
     Protože `$(TargetPath)` – makro vyjadřuje úplnou cestu ke spustitelnému souboru se `$(TargetPath)`.manifest určí manifestem aplikace vytvořeným v adresáři bin. Publikování zkopíruje tento manifest na umístění pro publikování, který jste nastavili dříve.  
  
8.  Znovu publikujte projekt. Přejděte **publikovat** stránky a klikněte na tlačítko **publikovat**.  
  
     Zobrazte manifest znovu. Zobrazit manifest, otevřete adresář publikovat, klikněte pravým tlačítkem na soubor, klikněte na tlačítko **otevřete s**vyberte **ze seznamu vyberte program**a potom klikněte na tlačítko **Poznámkový blok**.  
  
     Verze by nyní mělo:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Stránka události sestavení, Návrhář projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Dialogové okno Příkazový řádek události před sestavením události/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)



