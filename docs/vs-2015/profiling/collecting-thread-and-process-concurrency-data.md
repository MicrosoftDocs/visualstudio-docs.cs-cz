---
title: Shromažďování dat o souběžnosti vláken a procesů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568160"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Shromažďování dat o souběžnosti vláken a procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Metoda profilace nástroje pro profilaci Concurrency umožňuje shromažďovat data kolizí prostředků, která obsahují informace o každé události synchronizace, která způsobí, že funkce v profilované aplikaci bude čekat na přístup k prostředku.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Metodu profilace souběžnosti můžete zadat pomocí jednoho z následujících postupů:  
  
- Na první stránce průvodce profilování klikněte na **souběžnost** .  
  
- Na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu klikněte na **souběžnost**.  
  
- Na panelu nástrojů **prohlížeč výkonu** v seznamu **Metoda** klikněte na **souběžnost**.  
  
## <a name="common-tasks"></a>Obecné úlohy  
 Další možnosti můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_v relaci výkonu. Chcete-li otevřít toto dialogové okno:  
  
- V **prohlížeč výkonu**klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.  
  
  Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_při profilaci pomocí metody souběžnosti.  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|Na stránce **Obecné** zadejte podrobnosti o pojmenování generovaného souboru dat profilování (. vsp).|-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na stránce **spuštění** určete aplikaci, která má být spuštěna, pokud máte více projektů. exe v rámci vašeho řešení kódu.|-   [Postupy: Určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na stránce **interakce vrstev** přidejte data volání ADO.NET do běhu profilace.|-   [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|  
|Na stránce **čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které mají být přidány do dat profilování jako značky.|-   [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na stránce **Upřesnit** určete verzi modulu runtime .NET Framework k profilaci, pokud vaše aplikační moduly používají více verzí. Ve výchozím nastavení je první načtená verze profilovaná.|-   [Postupy: určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
