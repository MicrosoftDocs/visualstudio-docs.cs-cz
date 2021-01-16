---
title: Shromažďovat data souběžnosti procesu & procesů
description: K shromažďování dat o každé události synchronizace, která způsobí, že funkce čeká na přístup k prostředkům, použijte metodu profilace Nástroje pro profilaci Concurrency.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1f6d0dbc8c10c972957e2bcf8092d145bb3651c
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533742"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Shromažďování dat o souběžnosti vláken a procesů

Metoda profilace souběžného zpracování sady Visual Studio Nástroje pro profilaci umožňuje shromažďovat data kolizí prostředků, která obsahují informace o každé události synchronizace, která způsobí, že funkce v profilované aplikaci bude čekat na přístup k prostředku.

Metodu profilace souběžnosti můžete zadat pomocí jednoho z následujících postupů:

- Na první stránce průvodce profilování klikněte na **souběžnost** .
- Na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu klikněte na **souběžnost**.
- Na panelu nástrojů **prohlížeč výkonu** v seznamu **Metoda** klikněte na **souběžnost**.

## <a name="common-tasks"></a>Běžné úkoly

Další možnosti můžete zadat v dialogovém okně **stránky vlastností** _relace výkonu_ v relaci výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu** klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.

Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně **stránky vlastností** _relace výkonu_ při profilaci pomocí metody souběžnosti.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** zadejte podrobnosti o pojmenování generovaného souboru dat profilování (. vsp).|- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **spuštění** určete aplikaci, která má být spuštěna, pokud máte více projektů. exe v rámci vašeho řešení kódu.|- [Postupy: Určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stránce **interakce vrstev** přidejte data volání ADO.NET do běhu profilace.|- [Shromáždit data interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které mají být přidány do dat profilování jako značky.|- [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** určete verzi modulu runtime .NET Framework k profilaci, pokud vaše aplikační moduly používají více verzí. Ve výchozím nastavení je první načtená verze profilovaná.|- [Postupy: určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
