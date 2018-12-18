---
title: Zobrazení událostí s IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46113365b66a75d3f9e149181637c79068645ab
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542322"
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Zobrazení událostí s IntelliTrace v sadě Visual Studio
Nástroj IntelliTrace můžete použít ke shromažďování informací o určité události a kategorie událostí, nebo o voláních jednotlivé funkce kromě události. Následující postupy ukazují, jak to udělat.  
  
 Můžete použít nástroj IntelliTrace v sadě Visual Studio Enterprise edition, ale ne edice Professional nebo Community.  
  
##  <a name="GettingStarted"></a> Konfigurace technologie Intellitrace  
 Můžete zkusit ladění pouze události IntelliTrace. Mezi události IntelliTrace patří události ladicího programu, výjimky, události rozhraní .NET Framework a další systémové události. By měl zapnout nebo vypnout určité události k řízení událostí, které nástroj IntelliTrace zaznamenává před zahájením ladění. Další informace najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Zapněte události IntelliTrace pro přístup k souborům. Přejděte na **nástroje > Možnosti > Nástroje IntelliTrace > události IntelliTrace** stránce a rozbalte **souboru** kategorie. Zkontrolujte, **souboru** kategorie události. To způsobí, že všechny souboru události (přístup, zavřít, delete) která se má zkontrolovat.

## <a name="create-your-app"></a>Vytvoření aplikace
  
1.  Vytvořte konzolovou aplikaci C#. V souboru Program.cs přidejte následující `using` – příkaz:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Vytvoření <xref:System.IO.FileStream> v metodu Main, čtení z něj, zavřete ho a stejný soubor odstranit také. Přidáte další řádek, jen aby místo, kde můžete nastavit zarážku:  
  
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
  
3.  Nastavení zarážky v `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Spustit ladění a zobrazení události IntelliTrace
  
1.  Spusťte ladění obvyklým způsobem. (Stiskněte **F5** nebo klikněte na tlačítko **ladit > Spustit ladění**.  
  
    > [!TIP]
    >  Zachovat **lokální** a **automatické hodnoty** windows otevřete během ladění zobrazovat a poznamenejte si hodnoty v těchto oknech.  
  
2.  Provádění zastaví na zarážce. Pokud se nezobrazí **diagnostické nástroje** okna, klikněte na tlačítko **ladit > Windows > události IntelliTrace**.  
  
     V **diagnostické nástroje** okně Najít **události** kartu (3 karty, by se měla zobrazit **události**, **využití paměti**, a **procesoru Využití**). **Události** karta zobrazuje chronologický seznam událostí, s poslední událostí před přerušením provádění ladicí program. Měli byste vidět událost s názvem **přístup WordSearchInputs.txt**.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Vyberte událost rozbalíte její podrobnosti.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Můžete zvolením odkazu cesty otevřete soubor. Pokud není k dispozici, úplná cesta **otevřít soubor** zobrazí se dialogové okno.  
  
     Klikněte na tlačítko **aktivovat historické ladění**, který nastaví kontext ladicího programu na čas, kdy byla zvolená událost shromážděných, zobrazení historických dat **zásobník volání**, **místníchhodnot** a dalších zúčastněných ladicího programu systému windows. Pokud zdrojový kód je k dispozici, Visual Studio přesune ukazatel na odpovídající kód v okně zdroje tak, aby jej můžete prozkoumat.  
  
     Na následujícím snímku obrazovky je z Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
4.  Pokud jste nenašli chyba, zkuste zkoumání další události vedoucí k chybě. Můžete také mít IntelliTrace zaznamenávat informace o voláních, takže můžete krokovat volání funkcí. 
  
## <a name="next-steps"></a>Další kroky

Můžete použít některé pokročilé funkce IntelliTrace s historické ladění:

 - Chcete-li zobrazit snímků, najdete v článku [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md)
 - Zjistěte, jak kontrolovat proměnné a vyhledání kódu, naleznete v tématu [Kontrola aplikace s využitím historického ladění](../debugger/historical-debugging-inspect-app.md)