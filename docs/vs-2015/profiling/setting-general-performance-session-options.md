---
title: Relace výkonu nastavení obecných možností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63c4a255d972b16bd7d9fda3d6c5a0d27978595
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808424"
---
# <a name="setting-general-performance-session-options"></a>Nastavení obecných možností výkonnostní relace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit metodu shromažďování a data zásady vytváření názvů pro profilování [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] výkonnostní relace nástrojů pro profilaci na **Obecné** stránky dialogové okno Vlastnosti relace výkonu. Chcete-li otevřít toto dialogové okno z **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
 **Požadavky**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Výběr metody kolekce dat  
 Nastavte jako metodu základní kolekce tak, že vyberete jednu z možností v části **sběr dat profilace**. Tyto možnosti jsou popsány v následující tabulce:  
  
|||  
|-|-|  
|**Vzorkování**. Metoda vzorkování shromažďuje profilování informace v pravidelných intervalech. Tato metoda je užitečná pro vyhledání problémy s využitím procesoru a je navržený způsob spuštění většina vyšetřování výkonu.|-   [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentace**. Metoda instrumentace vkládá do kopie modulu profilace kód, který zaznamenává každou položku, ukončení a volání funkce funkce v modulu během profilování. Tato metoda je užitečná pro shromažďování podrobných informací o časování o části kódu a pochopení dopadu vstupních a výstupních operací na výkon aplikace.|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Souběžnost**. Za použití metody souběžnosti shromažďuje data pro každou událost, pozastaví spuštění kódu, například když vlákno čeká uzamčen přístup k prostředku aplikace k uvolnění. Tato metoda je užitečná pro analýzu vícevláknových aplikacích.|-   [Shromažďování dat souběžnosti proces a vlákna](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Můžete shromažďování dat paměti .NET pomocí metody vzorkování nebo instrumentace. Vyberte typ dat v rámci **profilování paměti .NET**.  
  
|||  
|-|-|  
|**Shromáždit informace o přidělování objektů .NET**. Ve výchozím nastavení data zahrnují počet a velikost přidělené objekty. Zaškrtněte nebo zrušte zaškrtnutí políčka Povolit nebo zakázat shromažďování dat paměti .NET.<br /><br /> **Také shromažďovat informace o životnosti objektů .NET**. Zaškrtněte toto políčko obsahují data o generací kolekce uvolňování paměti, které byly použity pro uvolnění paměti objektů.|-   [Shromažďuje alokaci paměti .NET a Data o životním cyklu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Stránka relace profilování se zobrazí, jakmile začnete profilovat aplikaci. Na této stránce můžete profilování pozastavit, obnovit a zastavit.  
  
 ![Stránce relace profilování](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>Nastavení možností datového souboru profilování  
  
|||  
|-|-|  
|**Sestava**. Ve výchozím nastavení souboru dat profilování (.vsp) je přiřazen název profilované aplikace a je umístěn ve složce řešení nebo projektu. Řetězec datum je také připojeným k názvu a zvyšující číslo je přidán do datových souborů, které by jinak mít duplicitní názvy. Tato nastavení můžete změnit.|-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|



