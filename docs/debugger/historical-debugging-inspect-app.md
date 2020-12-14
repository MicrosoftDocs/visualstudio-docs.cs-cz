---
title: Kontrola aplikace s historickým laděním | Microsoft Docs
description: Sledujte chybu v konzolové aplikaci v jazyce C#, která používá historické ladění IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d51327f67429071d08f6dfd02c0ec0a1fc55822f
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398698"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Kontrola aplikace pomocí IntelliTrace historické ladění v aplikaci Visual Studio (C#, Visual Basic, C++)

[Historické ladění](../debugger/historical-debugging.md) můžete použít k přesunu zpět a vpřed při provádění aplikace a kontrole jejího stavu.

IntelliTrace můžete použít v edici Visual Studio Enterprise Edition, ale ne v edicích Professional nebo Community.

## <a name="navigate-your-code-with-historical-debugging"></a>Navigace v kódu s historickým laděním

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

Předpokládáme, že očekávaná hodnota `resultInt` po volání `AddAll()` je 20 (výsledek násobení `testInt` 20 časů). (Předpokládáme také, že se chyba v nástroji nezobrazuje `AddInt()` ). Výsledek je ale ve skutečnosti 44. Jak můžeme najít chybu bez krokování po `AddAll()` dobu 10 krát? Pomocí historických ladění můžeme najít chybu rychleji a snadněji. Jak na to:

1. V **nabídce nástroje > možnosti > IntelliTrace > obecné**, ujistěte se, že je povolená možnost IntelliTrace, a vyberte **události IntelliTrace a informace o volání**. Pokud tuto možnost nevyberete, nebudete moci zobrazit navigační vazbu (jak je vysvětleno níže).

2. Nastavte zarážku na `Console.WriteLine(resultInt);` řádku.

3. Spuštění ladění Kód se spustí na zarážku. V okně **místní** hodnoty vidíte, že hodnota `resultInt` je 44.

4. Otevřete okno **diagnostické nástroje** (**ladění > zobrazit diagnostické nástroje**). Okno Code by mělo vypadat takto:

    ![Okno kódu na zarážce](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Měla by se zobrazit Dvojitá šipka vedle levého okraje, těsně nad zarážku. Tato oblast se nazývá navigační hřbet a používá se pro historické ladění. Klikněte na šipku.

    V okně kód byste měli vidět, že předchozí řádek kódu ( `int resultInt = AddIterative(testInt);` ) je barevně růžový. Nad oknem by se měla zobrazit zpráva, že jste teď v historickém ladění.

    Okno Code (kód) teď vypadá takto:

    ![okno Code v historickém režimu ladění](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Nyní se můžete krokovat s `AddAll()` metodou (**F11** nebo **krokem** na tlačítku v navigačním hřbetu). Krok nahoru (**F10** nebo **Přejít na další volání** v navigačním hřbetu. Růžová čára je nyní na `j = AddInt(j);` řádku. **F10** v tomto případě nekrokuje na další řádek kódu. Místo toho se postupuje na další volání funkce. Historické ladění přechází z volání na volání a přeskočí řádky kódu, které nezahrnují volání funkce.

7. Nyní proveďte krok do `AddInt()` metody. V tomto kódu by se měla zobrazit chyba hned.

## <a name="next-steps"></a>Další kroky

Tento postup právě poškrábaný plochu toho, co můžete dělat s historickým laděním.

- Pokud chcete zobrazit snímky během ladění, přečtěte si téma [Kontrola předchozích stavů aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md).
- Další informace o různých nastaveních a vlivech různých tlačítek na navigačním hřbetu najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).
