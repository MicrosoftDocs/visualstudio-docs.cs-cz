---
title: Shromažďuje alokaci paměti .NET a Data o životním cyklu | Dokumentace Microsoftu
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
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b31f4cfce52c60e4b8f65758fc56e16e29bef6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761575"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Shromažďování dat o alokaci paměti a době platnosti objektů .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci podporují kolekci alokaci paměti .NET a data o životním cyklu objektu, která vám pomůže zjistit problémy s výkonem souvisejících s pamětí ve vaší aplikaci.  
  
- Data o přidělování paměti .NET zahrnuje velikost a počet objektů paměti rozhraní .NET Framework, které byly přiděleny.  
  
- Data o životním cyklu objektu zahrnuje velikost a počet objektů paměti rozhraní .NET Framework, které byly získány zpět v tři generace uvolňování paměti kolekce.  
  
  **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 S použitím vzorkování nebo metoda profilace instrumentace lze shromažďovat data.  
  
-   Při použití metody vzorkování profileru sleduje všechna přidělení paměti .NET a objekty, které jsou vytvořeny procesem, který byl spuštěn, nebo připojené k.  
  
-   Při použití metody instrumentace profileru sleduje pouze přidělení paměti .NET a objekty, které jsou generovány instrumentované moduly.  
  
> [!IMPORTANT]
>  Při shromažďování dat paměti .NET (přidělení, správu životnosti objektů nebo obě) pomocí metody vzorkování, jsou ignorovány všechny události zadané uživatelem vzorkování a události přidělení paměti odpovídající slouží ke shromažďování dat.  
  
 Pokud jsou povolená profilace přidělování paměti of.NET také povolit zobrazení přidělení. Pokud povolíte profilace data o životním cyklu .NET, je také povolit zobrazení doby života objektů. Další informace najdete v tématu [přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md) a [zobrazení doby života objektu](../profiling/object-lifetime-view.md).  
  
 Informace o tom, jak shromažďování dat paměti .NET pomocí nástrojů příkazového řádku nástrojů pro profilaci najdete v tématu pomocí metod rozhraní .NET paměti shromažďovat přidělení paměti a životnosti objektů v [pomocí Profilování metody z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Ke shromažďování dat paměti .NET  
  
1.  V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2.  Na _relace výkonu_**stránky vlastností** dialogové okno, klikněte na tlačítko **Obecné** kartu a vyberte **.NET shromažďovat informace o přidělení paměti objektu** zaškrtávací políčko.  
  
3.  Chcete-li shromažďovat data o životním cyklu objektu rozhraní .NET, vyberte **také shromažďovat informace o životnosti objektů .NET** zaškrtávací políčko.  
  
## <a name="common-tasks"></a>Obecné úlohy  
 Můžete zadat další možnosti v _relace výkonu_**stránky vlastností** dialogovému oknu relace výkonu. Chcete-li otevřít toto dialogové okno:  
  
- V **prohlížeč výkonu**, klikněte pravým tlačítkem na název relace výkonu a potom klikněte na tlačítko **vlastnosti**.  
  
  Úkoly v následující tabulce popisují možnosti, které můžete určit _relace výkonu_**stránky vlastností** dialogové okno při shromažďování dat paměti .NET.  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|Na **Obecné** stránce, pojmenování detailů generovaného souboru dat profilování (.vsp).|-   [Shromažďuje alokaci paměti .NET a Data o životním cyklu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **spuštění** stránce, zvolte aplikaci, která spustit, pokud máte několik projektů .exe ve vašem kódu řešení.|-   [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|  
|Na **interakce vrstev** stránce, přidejte data pro volání ADO.NET pro spuštění profilování.|-   [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|  
|Na **události Windows** stránky, zadejte jeden nebo více událostí trasování událostí pro Windows (ETW) pro shromažďování dat prostřednictvím data vzorkování.|-   [Postupy: shromažďování trasování událostí pro Windows (ETW) dat.](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **čítače Windows** stránky, zadejte jeden nebo více čítačů výkonu operačního systému pro přidání do profilových dat. jako značky.|-   [Postupy: shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **Upřesnit** stránky, zadejte verzi modulu runtime rozhraní .NET Framework do profilu, pokud vaše aplikace moduly používat více verzí. Standardně je první verze načíst profilována.|-   [Postupy: určení modulu Runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Instrumentace úlohy  
 Úkoly v následující tabulce jsou možnosti **stránky vlastností** dialogové okno, které jsou specifické pro profilování pomocí metody instrumentace.  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|Na **binární soubory** stránky, zadejte umístění pro instrumentované kopie modulů. Ve výchozím nastavení původní binární soubory přesunou do složky pro zálohy.|-   [Postupy: přemístění instrumentovaných binárních souborů](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **instrumentace** stránce, malé funkce vyloučit z profilace ke snížení profilace režie, profil kódu jazyka JavaScript na webových stránkách ASP.NET a zadat příkazy před a po spuštění z příkazového řádku proces instrumentace.|-   [Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Postupy: profilování kódu JavaScript ve webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Postupy: určení příkazů k provedení před instrumentací a po instrumentaci](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **čítače CPU** stránky, zadejte jeden nebo více čítačů výkonu procesoru pro přidání do profilových dat.|-   [Postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **Upřesnit** stránky, zadejte jakékoli další VSInstr.exe požadované možnosti, jako je například možnost zahrnout nebo vyloučit určité funkce. Další informace o možnosti VSInstr najdete v tématu [VSInstr](../profiling/vsinstr.md)|-   [Postupy: určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Postupy: omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Postupy: výběr metod kolekcí](../profiling/how-to-choose-collection-methods.md)   
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)



