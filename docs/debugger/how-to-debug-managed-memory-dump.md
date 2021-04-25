---
title: Ladění spravovaného výpisu paměti pomocí diagnostických analyzátorů .NET | Microsoft Docs
description: Zjistěte, jak pomocí analyzátorů diagnostiky .NET sady Visual Studio analyzovat spravovaný výpis paměti.
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2021
ms.locfileid: "107952901"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>Postup ladění spravovaného výpisu paměti pomocí analyzátorů diagnostiky .NET



V tomto kurzu:

> [!div class="checklist"]
> * Otevření výpisu paměti
> * Vybrat a spustit analyzátory proti výpisu
> * Kontrola výsledků analyzátorů
> * Navigace s problematickým kódem


V příkladu popsaném v tomto článku je důležité, aby vaše aplikace včas nereagovala na žádosti. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Otevření výpisu paměti v aplikaci Visual Studio

1. Otevřete výpis paměti v aplikaci Visual Studio pomocí příkazu **soubor > otevřít > soubor** nabídky a vyberte výpis paměti.

1. Na stránce Souhrn výpisu paměti si všimněte nové **Akce** s názvem **Spustit analýzu diagnostiky**.

   ![Akce – analýza diagnostiky](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Tuto akci vyberte, pokud chcete spustit ladicí program a otevřete stránku Nová **Analýza diagnostiky** se seznamem dostupných možností analyzátoru uspořádaných podle základního příznaku.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Vybrat a spustit analyzátory proti výpisu

Aby bylo možné tyto příznaky prozkoumat, jsou nejlepší možnosti k dispozici v části **zpracování odezvy procesu** , protože nejlépe odpovídá problému v tomto příkladu.

   ![Vybrat analyzátory diagnostiky](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Kliknutím na tlačítko **analyzovat** spustíte proces zkoumání. 

1. Analyzátor bude prezentovat výsledky na základě kombinace informací o procesu a dat CLR zachycených v výpisu paměti.
 
## <a name="review-the-results-of-the-analyzers"></a>Kontrola výsledků analyzátorů

1. V tomto případě analyzátor našel dvě chyby. Vyberte výsledek analyzátoru, aby se zobrazil **Souhrn analýzy** a navrhovaná **náprava**.

   ![Výsledky analyzátorů diagnostiky](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. **Souhrn analýzy** uvedl, že "fond vláken CLR má vyčerpání". Tyto informace naznačují, že modul CLR aktuálně používá všechna dostupná vlákna fondu vláken, což znamená, že vaše služba nemůže reagovat na jakékoli nové požadavky, dokud se vlákno neuvolní.

    > [!NOTE] 
    > **Náprava** v tomto případě je "nesynchronně čekat na monitorování, události, úlohu nebo jiné objekty, které mohou blokovat vaše vlákno. Podívejte se, jestli můžete metodu aktualizovat tak, aby byla asynchronní. ".

## <a name="navigating-to-the-problematic-code"></a>Navigace s problematickým kódem

Moje další úloha slouží k vyhledání problematického kódu.

1. Kliknutím na odkaz **Zobrazit zásobník volání** Visual Studio se okamžitě přepne na vlákna, u kterých se toto chování projeví.

1. Okno **zásobník volání** zobrazí metody, které mohou potenciálně rychle rozlišovat mezi vlastními kódy (SyncOverAsyncExmple.*) z kódu Frameworku (System.*).

   ![Analyzátor diagnostiky – odkaz na zásobník volání](../debugger/media/diagnostic-analyzer-call-stack.png)

1. Každý rámec zásobníku volání odpovídá metodě a Poklikáním na snímky zásobníku sada Visual Studio přejde na kód, který vedlo přímo k tomuto scénáři v tomto vlákně.

1. V tomto příkladu nejsou k dispozici žádné symboly ani kód, ale na stránce **symboly nejsou načteny** můžete vybrat možnost **[dekompilovat zdrojový kód](../debugger/decompilation.md)** .

   ![Dekompilace](../debugger/media/diagnostic-analyzer-decompilation.png)

1. V dekompilovaném zdroji níže je zřejmé, že asynchronní úloha (ConsumeThreadPoolThread) volá synchronní blokující funkci.

    > [!NOTE]  
    > Metoda "DoSomething ()", která obsahuje metodu WaitHandle. WaitOne, která blokuje aktuální vlákno fondu vláken, dokud neobdrží signál.

   Pro zlepšení odezvy aplikací je důležité odebrat blokování synchronního kódu ze všech asynchronních kontextů.

   ![Analyzovat dekompilovaný kód](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Viz také

* [Použití souborů výpisu paměti v ladicím programu](../debugger/using-dump-files.md)
* [Generovat zdrojový kód ze sestavení .NET během ladění](../debugger/decompilation.md)
* [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
