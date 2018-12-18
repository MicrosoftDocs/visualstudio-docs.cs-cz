---
title: Historické ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d43e48b67cdbfabcb38703469f8570f78336dcab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794592"
---
# <a name="historical-debugging"></a>Historické ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Historické ladění je režim ladění, který závisí na informace shromážděné funkcí technologie IntelliTrace. Umožňuje přejít zpět a vpřed prostřednictvím spuštění vaší aplikace a zkontrolovat její stav.  
  
 Můžete použít nástroj IntelliTrace v sadě Visual Studio Enterprise edition (ale ne edice Professional nebo Community).  
  
## <a name="why-use-historical-debugging"></a>Proč používat historické ladění?  
 Nastavení zarážek, abyste odhalili chyby může být místo toho hit-or-miss záležitost. Nastavit zarážku blízko místa v kódu kde máte podezření na chybu na a pak spusťte aplikaci v ladicím programu a Doufáme, že zarážku získá přístupů a že na místě, kde se přeruší provádění může odhalit příčiny chyby. V opačném případě bude nutné vyzkoušet, nastavením zarážky někde jinde v kódu a znovu spusťte ladicí program, spuštění testovací kroky pořád dokola, dokud nalezení příčiny problému.  
  
 ![nastavením zarážky](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Můžete přesouvat kolem ve vaší aplikaci a zkontrolujte jeho stav (zásobník volání a místní proměnné) bez nutnosti nastavovat zarážky, restart ladění pomocí IntelliTrace a historické ladění a testovací kroky. To vám ušetří spoustu času, zejména při chyby se nachází hlouběji ve scénáři testu, která trvá dlouhou dobu spuštění.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Jak můžu začít používat historické ladění?  
 Nástroj IntelliTrace je ve výchozím. Všechno, co musíte udělat, je rozhodnout, které události nebo volání funkce jsou vás zajímají. Další informace o definování co chcete hledat, naleznete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md). Krok za krokem účet ladění pomocí nástroje IntelliTrace naleznete v tématu [návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Pohyb v kódu s historické ladění  
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
  
1. Nástroje / možnosti / IntelliTrace / Obecné, ujistěte se, že IntelliTrace zapnutý, události IntelliTrace a vyberte možnost informací o volání. Pokud tuto možnost nevyberete, nebudete moci zobrazit navigační ovládací prvek (jak je popsáno níže).  
  
2. Nastavit zarážku na `Console.WriteLine(resultInt);` řádku.  
  
3. Spusťte ladění. Kód se spustí až k zarážce. V **lokální** okně vidíte, že hodnota `resultInt` je 44.  
  
4. Otevřít **diagnostické nástroje** okno (**ladění / zobrazit diagnostické nástroje**). V okně kódu by měl vypadat nějak takto:  
  
    ![Okno kódu na zarážce](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Měli byste vidět dvojitou šipku vedle levého okraje, těsně nad zarážku. Tato oblast se nazývá navigační ovládací prvek a slouží pro historické ladění. Klikněte na šipku.  
  
    V okně kódu byste měli vidět, který na předchozí řádek kódu (`int resultInt = AddIterative(testInt);`) jsou zobrazeny růžový. Nad oknem měli byste vidět zprávu, která jsou teď v historické ladění.  
  
    V okně kódu nyní vypadá takto:  
  
    ![okno kódu v režimu historické ladění](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Nyní můžete krokovat s vnořením `AddAll()` – metoda (**F11**, nebo **Krokovat s vnořením** v navigační ovládací prvek tlačítko. Krok vpřed (**F10**, nebo **přejít na další volání** v navigační ovládací prvek. Růžový řádek je nyní na `j = AddInt(j);` řádku. **F10** v tomto případě Nekrokovat s vnořením na další řádek kódu. Místo toho se přejde na další volání funkce. Historické ladění přejde z volání do volání a přeskočí řádky kódu, které neobsahují volání funkce.  
  
7. Nyní můžete krokovat s vnořením `AddInt()` metody. V tomto kódu chyby byste měli vidět okamžitě.  
  
   Tento postup stačí poškrábaný na plochu můžete dělat s historické ladění. Další informace o různých nastavení a efekty různá tlačítka v navigační ovládací prvek, najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).





