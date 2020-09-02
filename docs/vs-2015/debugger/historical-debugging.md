---
title: Historické ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192191"
---
# <a name="historical-debugging"></a>Historické ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Historické ladění je režim ladění, který závisí na informacích shromažďovaných pomocí IntelliTrace. Umožňuje přesunout zpět a vpřed v průběhu provádění aplikace a zkontrolovat její stav.  
  
 IntelliTrace můžete použít v edici Visual Studio Enterprise (ale ne v edicích Professional nebo Community).  
  
## <a name="why-use-historical-debugging"></a>Proč používat historické ladění?  
 Nastavení zarážek pro hledání chyb může být místo toho Affair nebo neúspěšný. Nastavte zarážku blízko na místo v kódu, kde máte podezření, že se jedná o chybu, potom spusťte aplikaci v ladicím programu a doufáme, že se zarážka spustí, a že místo, kde se přerušení provádění může odhalit zdroj chyby. V opačném případě budete muset zkusit nastavit zarážku někde jinde v kódu a znovu spustit ladicí program, který provede testovací kroky před a nad, dokud problém nezjistíte.  
  
 ![Nastavení zarážky](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Můžete použít IntelliTrace a historické ladění pro pohyb v aplikaci a zkontrolovat její stav (zásobník volání a místní proměnné) bez nutnosti nastavovat zarážky, znovu spustit ladění a opakovat kroky testu. To vám může ušetřit spoustu času, zejména v případě, že se chyba nachází hluboko v testovacím scénáři, který trvá dlouhou dobu.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Návody začít používat historické ladění?  
 IntelliTrace je ve výchozím nastavení zapnuté. Stačí se rozhodnout, které události a volání funkcí vás zajímají. Další informace o tom, jak definovat, co chcete vyhledat, najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md). Podrobný účet pro ladění pomocí IntelliTrace naleznete v tématu [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Navigace v kódu s historickým laděním  
 Pojďme začít jednoduchým programem, který obsahuje chybu. Do konzolové aplikace v jazyce C# přidejte následující kód:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Předpokládáme, že očekávaná hodnota `resultInt` po volání `AddAll()` je 20 (výsledek násobení `testInt` 20 časů). (Předpokládáme také, že se chyba v nástroji nezobrazuje `AddInt()` ). Výsledek je ale ve skutečnosti 44. Jak můžeme najít chybu bez krokování po `AddAll()` dobu 10 krát? Pomocí historických ladění můžeme najít chybu rychleji a snadněji. Postupujte následovně:  
  
1. V nabídce Nástroje/možnosti/IntelliTrace/obecné se ujistěte, že je povolený IntelliTrace, a vyberte možnost události IntelliTrace a informace o volání. Pokud tuto možnost nevyberete, nebudete moci zobrazit navigační vazbu (jak je vysvětleno níže).  
  
2. Nastavte zarážku na `Console.WriteLine(resultInt);` řádku.  
  
3. Spuštění ladění Kód se spustí na zarážku. V okně **místní** hodnoty vidíte, že hodnota `resultInt` je 44.  
  
4. Otevřete okno **diagnostické nástroje** (**ladění/zobrazit diagnostické nástroje**). Okno Code by mělo vypadat takto:  
  
    ![Okno kódu na zarážce](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Měla by se zobrazit Dvojitá šipka vedle levého okraje, těsně nad zarážku. Tato oblast se nazývá navigační hřbet a používá se pro historické ladění. Klikněte na šipku.  
  
    V okně kód byste měli vidět, že předchozí řádek kódu ( `int resultInt = AddIterative(testInt);` ) je barevně růžový. Nad oknem by se měla zobrazit zpráva, že jste teď v historickém ladění.  
  
    Okno Code (kód) teď vypadá takto:  
  
    ![okno Code v historickém režimu ladění](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Nyní se můžete krokovat s `AddAll()` metodou (**F11**nebo **krokem** na tlačítku v navigačním hřbetu). Krok nahoru (**F10**nebo **Přejít na další volání** v navigačním hřbetu. Růžová čára je nyní na `j = AddInt(j);` řádku. **F10** v tomto případě nekrokuje na další řádek kódu. Místo toho se postupuje na další volání funkce. Historické ladění přechází z volání na volání a přeskočí řádky kódu, které nezahrnují volání funkce.  
  
7. Nyní proveďte krok do `AddInt()` metody. V tomto kódu by se měla zobrazit chyba hned.  
  
   Tento postup právě poškrábaný plochu toho, co můžete dělat s historickým laděním. Další informace o různých nastaveních a vlivech různých tlačítek na navigačním hřbetu najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).
