---
title: Kontrola aplikace s využitím historického ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2309a3213344607fa0f5b2f626fc67af2eff8f79
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542335"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Kontrola aplikace s použitím technologie IntelliTrace historické ladění v sadě Visual Studio
Můžete použít [historické ladění](../debugger/historical-debugging.md) pro přechod dozadu a předání prostřednictvím spuštění vaší aplikace a zkontrolovat její stav.  
  
Můžete použít nástroj IntelliTrace v sadě Visual Studio Enterprise edition, ale není edice Professional nebo Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Navigace v kódu s historické ladění  
 Začněme jednoduchý program, který obsahuje chybu. V aplikaci konzoly C# přidejte následující kód:  
  
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
  
 Budeme předpokládat, který očekávanou hodnotou `resultInt` po volání `AddAll()` je 20 (výsledek zvyšování `testInt` 20 x). (Budete také předpokládáme, že nevidíte chybu v `AddInt()`). Ale ve skutečnosti 44 je výsledek. Jak jsme najít chyby bez krokování `AddAll()` 10krát? Můžeme použít historické ladění najít chyby rychleji a snadněji. Tady je způsob:  
  
1.  V **nástroje > Možnosti > Nástroje IntelliTrace > Obecné**, ujistěte se, že nástroj IntelliTrace zapnutý a vyberte **události IntelliTrace a informací o volání**. Pokud tuto možnost nevyberete, nebudete moci zobrazit navigační ovládací prvek (jak je popsáno níže).  
  
2.  Nastavit zarážku na `Console.WriteLine(resultInt);` řádku.  
  
3.  Spusťte ladění. Kód se spustí až k zarážce. V **lokální** okně vidíte, že hodnota `resultInt` je 44.  
  
4.  Otevřít **diagnostické nástroje** okno (**ladit > zobrazit diagnostické nástroje**). V okně kódu by měl vypadat nějak takto:  
  
     ![Okno kódu na zarážce](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Měli byste vidět dvojitou šipku vedle levého okraje, těsně nad zarážku. Tato oblast se nazývá navigační ovládací prvek a slouží pro historické ladění. Klikněte na šipku.  
  
     V okně kódu byste měli vidět, který na předchozí řádek kódu (`int resultInt = AddIterative(testInt);`) jsou zobrazeny růžový. Nad oknem měli byste vidět zprávu, která jsou teď v historické ladění.  
  
     V okně kódu nyní vypadá takto:  
  
     ![okno kódu v režimu historické ladění](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Nyní můžete krokovat s vnořením `AddAll()` – metoda (**F11**, nebo **Krokovat s vnořením** v navigační ovládací prvek tlačítko. Krok vpřed (**F10**, nebo **přejít na další volání** v navigační ovládací prvek. Růžový řádek je nyní na `j = AddInt(j);` řádku. **F10** v tomto případě Nekrokovat s vnořením na další řádek kódu. Místo toho se přejde na další volání funkce. Historické ladění přejde z volání do volání a přeskočí řádky kódu, které neobsahují volání funkce.  
  
7.  Nyní můžete krokovat s vnořením `AddInt()` metody. V tomto kódu chyby byste měli vidět okamžitě.  

## <a name="next-steps"></a>Další kroky

Tento postup stačí poškrábaný na plochu můžete dělat s historické ladění.

- Chcete-li zobrazit při ladění snímků, najdete v článku [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md).
- Další informace o různých nastavení a efekty různá tlačítka v navigační ovládací prvek, najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).