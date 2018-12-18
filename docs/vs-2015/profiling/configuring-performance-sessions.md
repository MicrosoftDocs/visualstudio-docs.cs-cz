---
title: Konfigurace výkonnostních relací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 280d9023167b4d83dfb8b0137301219a518521b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790393"
---
# <a name="configuring-performance-sessions"></a>Konfigurace výkonnostních relací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S použitím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje pro profilaci, můžete shromažďovat celou řadu údaje o výkonu pro mnoho typů aplikací. Tato část ukazuje, jak používat výkonu Wizardand vlastnosti relace výkonu a cílový binární soubor ke konfiguraci nástroje pro profilaci sady ke shromažďování dat, která vás zajímá. Vlastnosti konfigurace nástroje pro profilaci můžete použít také k řízení množství dat shromažďovaných během spuštění profilování. Další informace najdete v tématu [řízení shromažďování dat](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  V mnoha případech použití výchozí vlastnosti Průvodce výkonu je efektivní způsob shromažďování dat profilování. Další informace najdete v tématu [Průvodce začátečníka profilací výkonu](../profiling/beginners-guide-to-performance-profiling.md) a [Začínáme](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Nastavení základní profilování:** byste měli nakonfigurovat [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] používat Microsoft symbol server. Tím zajistíte, že máte přístup k symbolům, jako je například funkce a parametr názvy pro aktuální verzi Windows a jiné aplikace od Microsoftu. Další obecné možnosti můžete také určit před spuštěním relace profilování, jako jsou oprávnění systému a nástrojů pro profilaci a názvy souborů dat profilování.|-   [Postupy: referenční informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Postupy: serializace informací o symbolu](../profiling/how-to-serialize-symbol-information.md)<br />-   [Postupy: nastavení aktuální relace](../profiling/how-to-set-the-current-session.md)<br />-   [Postupy: nastavení oprávnění](../profiling/how-to-set-permissions.md)<br />-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Zadejte data, která chcete shromažďovat:** postupy, které můžete použít ke konfiguraci relace profilování se liší podle typu cílovou aplikaci, kterou chcete do profilu a typ, který chcete shromáždit údaje o výkonu.|-   [Postupy: výběr metod kolekcí](../profiling/how-to-choose-collection-methods.md)<br />-   [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Shromažďuje alokaci paměti .NET a Data o životním cyklu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Postupy: profilování kódu JavaScript ve webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Shromažďování dat souběžnosti proces a vlákna](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Shromažďování dalších dat o výkonu](../profiling/collecting-additional-performance-data.md)|  
|**Nastavit možnosti pokročilé konfigurace:** při profilování aplikace rozhraní .NET Framework, které načítají více verzí common language runtime (CLR), můžete určit, kterou verzi profilu. Pokud máte víc souborů .exe v relaci výkonu, můžete nastavit pořadí spouštění binárních souborů.|-   [Postupy: určení modulu Runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Postupy: určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Související oddíly  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)



