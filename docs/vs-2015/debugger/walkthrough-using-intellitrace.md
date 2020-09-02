---
title: 'Návod: použití IntelliTrace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64844165"
---
# <a name="walkthrough-using-intellitrace"></a>Postup: Použití IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace můžete použít ke shromažďování informací o konkrétních událostech nebo kategoriích událostí nebo o jednotlivých voláních funkcí kromě událostí. Následující postupy ukazují, jak to provést.  
  
 IntelliTrace můžete použít v edici Visual Studio Enterprise (ale ne v edicích Professional nebo Community).  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> Použití IntelliTrace jenom s událostmi  
 Můžete vyzkoušet ladění s pouhými IntelliTrace událostmi. Události IntelliTrace jsou události ladicího programu, výjimky, události .NET Framework a další systémové události. Můžete zapnout nebo vypnout konkrétní události pro řízení událostí, které IntelliTrace záznamy před spuštěním ladění. Další informace najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
 Následující kroky ukazují, jak ladit jenom události IntelliTrace:  
  
1. Zapněte událost IntelliTrace pro přístup k souboru. Otevřete stránku **události nástroje/možnosti/IntelliTrace/IntelliTrace** a rozbalte kategorii **soubor** . Podívejte se do kategorie událost **souboru** . Dojde k tomu ke zkontrolování všech událostí souboru (přístup, zavření, odstranění).  
  
2. Vytvořte konzolovou aplikaci C#. Do souboru Program.cs přidejte následující `using` příkaz:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Vytvořte <xref:System.IO.FileStream> v metodě Main, přečtěte si z něho, zavřete ho a odstraňte soubor. Přidat další řádek, který má místo pro nastavení zarážky:  
  
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
  
4. Nastavit zarážku na `Console.WriteLine("done");`  
  
5. Spusťte ladění obvyklým způsobem. (Stiskněte klávesu **F5** nebo klikněte na **ladění/spustit ladění**.  
  
    > [!TIP]
    > Nechte okna **místní** hodnoty a **Automatické** hodnoty otevřené, zatímco provádíte ladění, abyste mohli zobrazit a zaznamenat hodnoty v těchto oknech.  
  
6. Spuštění se zastaví na zarážce. Pokud nevidíte okno **diagnostické nástroje** , klikněte na **ladění/Windows/IntelliTrace události**.  
  
     V okně **diagnostické nástroje** Najděte kartu **události** (měli byste vidět 3 karty, **události**, **využití paměti**a **využití CPU**). Karta **události** zobrazuje chronologický seznam událostí končící poslední událostí před spuštěním ladicího programu podařilo přerušit. Měla by se zobrazit událost s názvem **Access WordSearchInputs.txt**.  
  
     Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;-datum1](../debugger/media/intellitrace-update1.png "IntelliTrace-v-datum1")  
  
7. Výběrem události rozbalíte její podrobnosti.  
  
     Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Můžete zvolit odkaz cesta k otevření souboru. Pokud úplná cesta není k dispozici, zobrazí se dialogové okno **otevřít soubor** .  
  
     Klikněte na **aktivovat historické ladění**, které nastaví kontext ladicího programu na čas, kdy se vybraná událost shromáždila, zobrazí se historická data v **zásobníku volání**, **místní** a ostatní okna zapojeného ladicího programu. Pokud je zdrojový kód k dispozici, Visual Studio přesune ukazatel na odpovídající kód v okně zdrojového kódu, abyste ho mohli prohlédnout.  
  
     Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;-datum1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-v-datum1")  
  
8. Pokud jste tuto chybu nenalezli, zkuste zkoumat další události, které se zavedou k chybě. IntelliTrace můžete také zaznamenat informace o volání, abyste mohli krokovat prostřednictvím volání funkcí.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Použití IntelliTrace s událostmi a voláními funkcí  
 IntelliTrace může nahrávat volání funkcí spolu s událostmi. To vám umožní zobrazit historii zásobníku volání a krokovat zpět a vpřed prostřednictvím volání ve vašem kódu. IntelliTrace zaznamenává data, jako jsou názvy funkcí, vstupní a výstupní body funkce a některé hodnoty parametrů a návratové hodnoty. Viz [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
1. Zapněte shromažďování volání. (V nabídce **Nástroje/možnosti/IntelliTrace/obecné**vyberte **události IntelliTrace a informace o volání**. IntelliTrace začne shromažďovat tyto informace při spuštění další relace ladění.  
  
    > [!TIP]
    > To může zpomalit vaši aplikaci a zvětšit velikost všech souborů protokolu IntelliTrace (soubory. iTrace), které ukládáte na disk. Abyste získali nejvíc dat volání, ale minimalizovali účinky, zaznamenejte data pouze z těch modulů, které vás zajímají. Chcete-li změnit maximální velikost souborů. iTrace, přejděte na **Nástroje/možnosti/IntelliTrace/Upřesnit**a zadejte maximální množství místa na disku. Výchozí hodnota je 250 MB.  
  
2. Spusťte ladění konzolové aplikace v jazyce C# vytvořené v předchozí části. Spuštění se zastaví na zarážce. Pokud nevidíte okno **diagnostické nástroje** , klikněte na **ladění/Windows/IntelliTrace události**.  
  
3. Přepněte na kartu **volání** .  
  
     Nyní vidíte volání funkcí vaší aplikace, počínaje kořenovým voláním (v aktuálním řešení, hlavním vstupním bodem) a končící umístěním, kde podařilo přerušit provádění.  
  
     Vyberte jedno z volání funkce a dvakrát na ni klikněte. Měli byste vidět vstupní a výstupní body funkce a také volání, která aktuální volání provedla jiným funkcím a události IntelliTrace vyvolané voláním. Pokud nemáte zapnuté historické ladění, tato akce se zapne. Další informace o historických ladění naleznete v tématu [historická ladění](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > Můžou se zobrazit informace o tom, že některá volání nejsou k dispozici. Důvodem je to, že IntelliTrace nezaznamenává data z odpovídajících modulů. Chcete-li zobrazit tato data, IntelliTrace shromažďovat data z těchto modulů. Informace o zadávání modulů najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Další kroky
