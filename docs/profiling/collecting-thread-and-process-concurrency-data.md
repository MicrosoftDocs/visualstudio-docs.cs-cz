---
title: Shromažďování dat souběžnosti procesu a vlákně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8ce2c1d7a28eff441cbf3a95e8f9df644789e70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775546"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Shromažďování dat o souběžnosti vláken a procesů

Metoda profilace souběžného zpracování profilování nástroje sady Visual Studio umožňuje shromažďovat data kolize prostředků, který obsahuje informace o každé synchronizaci událost, která způsobí, že funkce v profilované aplikace čekání na přístup k prostředku.

Můžete zadat souběžnosti metoda profilace pomocí jedné z následujících postupů:

- Klikněte na první stránce průvodce Profilováním, **souběžnosti**
- Na **Obecné** stránky dialogovém okně Vlastnosti relace výkonu můžete kliknout na tlačítko **souběžnosti**.
- Na **prohlížeč výkonu** nástrojů v **metoda** klikněte na možnost **souběžnosti**.

## <a name="common-tasks"></a>Běžné úlohy

Můžete zadat další možnosti v _relace výkonu_**stránky vlastností** dialogovému oknu relace výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu**, klikněte pravým tlačítkem na název relace výkonu a potom klikněte na tlačítko **vlastnosti**.

Úkoly v následující tabulce popisují možnosti, které můžete určit _relace výkonu_**stránky vlastností** dialogové okno při profilování pomocí za použití metody souběžnosti.

|Úloha|Související obsah|
|----------|---------------------|
|Na **Obecné** stránce, pojmenování detailů generovaného souboru dat profilování (.vsp).|- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **spuštění** stránky, zadejte aplikaci spustit, pokud máte několik projektů .exe ve vašem kódu řešení.|- [Postupy: určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)|
|Na **interakce vrstev** stránce, přidejte data pro volání ADO.NET pro spuštění profilování.|- [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na **čítače Windows** stránky, zadejte jeden nebo více čítačů výkonu operačního systému pro přidání do profilových dat. jako značky.|- [Postupy: shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **Upřesnit** stránky, zadejte verzi rozhraní .NET Framework doba běhu do profilu, pokud moduly vaše aplikace používat více verzí. Standardně je první verze načíst profilována.|- [Postupy: určení modulu runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|