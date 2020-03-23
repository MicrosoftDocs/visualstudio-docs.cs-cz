---
title: Shromažďování dat souběžnosti vláken a procesů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e8fda0300aad4a331366fac0a9ebd1b559cecc9d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779516"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Shromažďování dat o souběžnosti vláken a procesů

Visual Studio Profilování Nástroje souběžnosti profilování metoda umožňuje shromažďovat data tvrzení o prostředku, která obsahuje informace o každé události synchronizace, která způsobí, že funkce v profilované aplikaci čekat na přístup k prostředku.

Metodu profilování souběžnosti můžete určit pomocí jednoho z následujících postupů:

- Na první stránce Průvodce profilováním klikněte na **Souběžnost.**
- Na stránce **Obecné** v dialogovém okně vlastností relace výkonu klepněte na tlačítko **Souběžnost**.
- Na panelu nástrojů **Průzkumník výkonu** klikněte v seznamu **Metoda** na **možnost Souběžnost**.

## <a name="common-tasks"></a>Běžné úkoly

Další možnosti můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_relace výkonu. Otevření tohoto dialogového okna:

- V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na název relace výkonu a potom klepněte na příkaz **Vlastnosti**.

Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_při profilování pomocí metody souběžnosti.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** zadejte podrobnosti pojmenování pro soubor generateovaných profilování (.vsp).|- [Postup: Nastavení možností názvu souboru dat o výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **Spuštění** zadejte aplikaci, která má být spuštěna, pokud máte v řešení kódu více projektů .exe.|- [Postup: Zadejte binární soubor, který má být zahájen](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stránce **Interakce s vrstvou** přidejte ADO.NET data volání do spuštění profilování.|- [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které chcete přidat k datům profilování jako značky.|- [Postup: Shromažďování dat čítačů systému Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** zadejte verzi modulu run-time rozhraní .NET Framework do profilu, pokud moduly aplikace používají více verzí. Ve výchozím nastavení je profilována první načtená verze.|- [Postup: Určení runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
