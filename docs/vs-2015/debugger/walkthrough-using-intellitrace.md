---
title: 'Návod: Použití IntelliTrace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1e2b40e16a14da505243aeb11542df3adfb18d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781306"
---
# <a name="walkthrough-using-intellitrace"></a>Postup: Použití IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj IntelliTrace můžete použít ke shromažďování informací o určité události a kategorie událostí, nebo o voláních jednotlivé funkce kromě události. Následující postupy ukazují, jak to udělat.  
  
 Můžete použít nástroj IntelliTrace v sadě Visual Studio Enterprise edition (ale ne edice Professional nebo Community).  
  
##  <a name="GettingStarted"></a> Pomocí IntelliTrace pouze pomocí událostí  
 Můžete zkusit ladění pouze události IntelliTrace. Mezi události IntelliTrace patří události ladicího programu, výjimky, události rozhraní .NET Framework a další systémové události. By měl zapnout nebo vypnout určité události k řízení událostí, které nástroj IntelliTrace zaznamenává před zahájením ladění. Další informace najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
 Následující kroky ukazují, jak ladit pouze pomocí událostí IntelliTrace:  
  
1.  Zapněte události IntelliTrace pro přístup k souborům. Přejděte na **nástroje / Možnosti / IntelliTrace nebo události IntelliTrace** stránce a rozbalte **souboru** kategorie. Zkontrolujte, **souboru** kategorie události. To způsobí, že všechny souboru události (přístup, zavřít, delete) která se má zkontrolovat.  
  
2.  Vytvořte konzolovou aplikaci C#. V souboru Program.cs přidejte následující `using` – příkaz:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3.  Vytvoření <xref:System.IO.FileStream> v metodu Main, čtení z něj, zavřete ho a stejný soubor odstranit také. Přidáte další řádek, jen aby místo, kde můžete nastavit zarážku:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
4.  Nastavení zarážky v `Console.WriteLine("done");`  
  
5.  Spusťte ladění obvyklým způsobem. (Stiskněte **F5** nebo klikněte na tlačítko **ladění / spuštění ladění**.  
  
    > [!TIP]
    >  Zachovat **lokální** a **automatické hodnoty** windows otevřete během ladění zobrazovat a poznamenejte si hodnoty v těchto oknech.  
  
6.  Provádění zastaví na zarážce. Pokud se nezobrazí **diagnostické nástroje** okna, klikněte na tlačítko **ladění / Windows / události IntelliTrace**.  
  
     V **diagnostické nástroje** okně Najít **události** kartu (3 karty, by se měla zobrazit **události**, **využití paměti**, a **procesoru Využití**). **Události** karta zobrazuje chronologický seznam událostí, s poslední událostí před přerušením provádění ladicí program. Měli byste vidět událost s názvem **přístup WordSearchInputs.txt**.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
7.  Vyberte událost rozbalíte její podrobnosti.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Můžete zvolením odkazu cesty otevřete soubor. Pokud není k dispozici, úplná cesta **otevřít soubor** zobrazí se dialogové okno.  
  
     Klikněte na tlačítko **aktivovat historické ladění**, který nastaví kontext ladicího programu na čas, kdy byla zvolená událost shromážděných, zobrazení historických dat **zásobník volání**, **místníchhodnot** a dalších zúčastněných ladicího programu systému windows. Pokud zdrojový kód je k dispozici, Visual Studio přesune ukazatel na odpovídající kód v okně zdroje tak, aby jej můžete prozkoumat.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
8.  Pokud jste nenašli chyba, zkuste zkoumání další události vedoucí k chybě. Můžete také mít IntelliTrace zaznamenávat informace o voláních, takže můžete krokovat volání funkcí.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Pomocí IntelliTrace s událostmi a volání funkcí  
 Nástroj IntelliTrace umí zaznamenat volání funkce spolu s událostmi. To umožňuje zobrazit historii zásobníku volání, krokovat zpět a vpřed mezi voláními ve vašem kódu. Nástroj IntelliTrace zaznamenává data, jako jsou názvy funkcí, funkce vstupní a výstupní body a některé hodnoty parametrů a návratové hodnoty. Zobrazit [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
1.  Zapněte shromažďování dat volání. (Na **nástroje / Možnosti / IntelliTrace / Obecné**vyberte **události IntelliTrace a informací o volání**. IntelliTrace se spustí shromažďování těchto informací při spuštění další relace ladění.  
  
    > [!TIP]
    >  To může zpomalit vaši aplikaci a zvětšit velikost všech protokolů souborů IntelliTrace (.iTrace) ukládaných na disk. Chcete-li získat většinu dat volání, ale minimalizování negativních dopadů, zaznamenávejte data z pouze modulů, které vás zajímají. Chcete-li změnit maximální velikost souborů .iTrace, přejděte na **nástroje / Možnosti / IntelliTrace / pokročilé**a zadat maximální množství místa na disku. Výchozí hodnota je 250 MB.  
  
2.  Spusťte ladění konzolovou aplikaci C# vytvořené v předchozí části. Provádění zastaví na zarážce. Pokud se nezobrazí **diagnostické nástroje** okna, klikněte na tlačítko **ladění / Windows / události IntelliTrace**.  
  
3.  Přepněte **volání** kartu.  
  
     Teď vidíte volání funkce vaší aplikace, počínaje kořenovým voláním (v aktuálním řešení hlavní vstupní bod) a končící na umístění, které provádění přerušilo.  
  
     Vyberte jednu z volání funkce a dvojím kliknutím ho. Měli byste vidět funkce vstupní a výstupní body, jakož i volání, že aktuální volání dalších funkcí a IntelliTrace události vyvolané službou volání. Pokud nemáte historické ladění zapnuté, tato akce zapne ho. Další informace o historické ladění, naleznete v tématu [historické ladění](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    >  Uvidíte, že některá volání jsou neaktivní. Je to proto, že nástroj IntelliTrace nezaznamenal data z odpovídajících modulů. Pro zobrazení těchto dat, nástroj IntelliTrace na shromažďování dat z těchto modulů. Informace o zadávání moduly, naleznete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Další kroky






