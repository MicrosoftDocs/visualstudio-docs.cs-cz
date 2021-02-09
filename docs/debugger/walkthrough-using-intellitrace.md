---
title: Zobrazení událostí s IntelliTrace | Microsoft Docs
description: Naučte se používat IntelliTrace v Visual Studio Enterprise ke shromažďování dat o konkrétních událostech, kategoriích událostí a jednotlivých voláních funkcí.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8adaf62d7a9995bb5219d340e0e9a9999055c7a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884075"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Zobrazení událostí s IntelliTrace v Visual Studio Enterprise (C#, Visual Basic)

IntelliTrace můžete použít ke shromažďování informací o konkrétních událostech nebo kategoriích událostí nebo o jednotlivých voláních funkcí kromě událostí. Následující postupy ukazují, jak to provést.

IntelliTrace můžete použít v edici Visual Studio Enterprise, ale ne v edicích Professional nebo Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Konfigurace IntelliTrace

Můžete vyzkoušet ladění s pouhými IntelliTrace událostmi. Události IntelliTrace jsou události ladicího programu, výjimky, události .NET Framework a další systémové události. Můžete zapnout nebo vypnout konkrétní události pro řízení událostí, které IntelliTrace záznamy před spuštěním ladění. Další informace najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).

- Zapněte událost IntelliTrace pro přístup k souboru. V **nabídce nástroje > možnosti > IntelliTrace > události IntelliTrace** a rozbalte kategorii **soubor** . Podívejte se do kategorie událost **souboru** . Dojde k tomu ke zkontrolování všech událostí souboru (přístup, zavření, odstranění).

## <a name="create-your-app"></a>Vytvoření aplikace

1. Vytvořte konzolovou aplikaci C#. Do souboru Program.cs přidejte následující `using` příkaz:

    ```csharp
    using System.IO;
    ```

2. Vytvořte <xref:System.IO.FileStream> v metodě Main, přečtěte si z něho, zavřete ho a odstraňte soubor. Přidat další řádek, který má místo pro nastavení zarážky:

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

3. Nastavit zarážku na `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Spuštění ladění a zobrazení událostí IntelliTrace

1. Spusťte ladění obvyklým způsobem. (Stiskněte klávesu **F5** nebo klikněte na **ladění > spustit ladění**.)

    > [!TIP]
    > Nechte okna **místní** hodnoty a **Automatické** hodnoty otevřené, zatímco provádíte ladění, abyste mohli zobrazit a zaznamenat hodnoty v těchto oknech.

2. Spuštění se zastaví na zarážce. Pokud nevidíte okno **diagnostické nástroje** , klikněte na **ladění > Windows > IntelliTrace události**.

    V okně **diagnostické nástroje** Najděte kartu **události** (měli byste vidět 3 karty, **události**, **využití paměti** a **využití CPU**). Karta **události** zobrazuje chronologický seznam událostí končící poslední událostí před spuštěním ladicího programu podařilo přerušit. Měla by se zobrazit událost s názvem **Access WordSearchInputs.txt**.

    Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.

    ![Snímek obrazovky okna Visual Studio Code Spuštění je zastaveno na zarážce a karta události v okně Diagnostické nástroje vypisuje události.](../debugger/media/intellitrace-update1.png)

3. Výběrem události rozbalíte její podrobnosti.

    Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.

    ![Snímek obrazovky karty události v okně Diagnostické nástroje sady Visual Studio. Vybere se událost, která se rozbalí, aby se zobrazila její podrobnosti.](../debugger/media/intellitraceupdate1-singleevent.png)

    Můžete zvolit odkaz cesta k otevření souboru. Pokud úplná cesta není k dispozici, zobrazí se dialogové okno **otevřít soubor** .

    Klikněte na **aktivovat historické ladění**, které nastaví kontext ladicího programu na čas, kdy se vybraná událost shromáždila, zobrazí se historická data v **zásobníku volání**, **místní** a ostatní okna zapojeného ladicího programu. Pokud je zdrojový kód k dispozici, Visual Studio přesune ukazatel na odpovídající kód v okně zdrojového kódu, abyste ho mohli prohlédnout.

    Následující snímek obrazovky je ze sady Visual Studio 2015 Update 1.

    ![Snímek obrazovky okna Visual Studio Code Spuštění je zastaveno na zarážce, je vybrána událost a odpovídající řádek kódu je zvýrazněn.](../debugger/media/historicaldebugging-update1.png)

4. Pokud jste tuto chybu nenalezli, zkuste zkoumat další události, které se zavedou k chybě. IntelliTrace můžete také zaznamenat informace o volání, abyste mohli krokovat prostřednictvím volání funkcí.

## <a name="next-steps"></a>Další kroky

Můžete použít některé z pokročilých funkcí IntelliTrace s historickým laděním:

- Pokud chcete zobrazit snímky, přečtěte si téma [Kontrola předchozích stavů aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md) .
- Informace o tom, jak kontrolovat proměnné a procházet kód, najdete v tématu [Kontrola aplikace pomocí historických ladění](../debugger/historical-debugging-inspect-app.md) .
