---
title: Vlastnosti výkonnostní relace | Dokumentace Microsoftu
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
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed020d09bc3c7b85a395625f410f0062bf4bfac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739277"
---
# <a name="performance-session-properties"></a>Vlastnosti výkonnostní relace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A **relace výkonu** vám umožní nakonfigurovat nastavení, která určují, jak je aplikace profilována. Také ukládá sestavy, které jsou generovány pro relaci profilování.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Vytváření **relace výkonu** spuštěním **Průvodce výkonem** nebo ručně vytvořit relaci. **Relace výkonu** se zobrazí v **prohlížeč výkonu** po **relace výkonu** se vytvořil.  
  
  Chcete-li zobrazit **relace výkonu** vlastnosti, vyberte název relace v **prohlížeč výkonu**, pravým tlačítkem myši a potom vyberte **vlastnosti**.  
  
  Relace výkonu má následující stránky vlastností:  
  
## <a name="general"></a>Obecné  
 Tato nastavení umožňují vybrat metoda pro přidání kolekce objektů .NET a data o životním cyklu a k určení umístění výchozí sestavy profilování a pojmenování konvence.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)  
  
 [Shromažďování dat o přidělení paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Postupy: Nastavení možností názvu souboru s údaji o výkonu](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Spuštění  
 Tato nastavení umožňují vybrat ze seznamu binárních souborů a určete pořadí spouštění binárních souborů.  
  
 Další informace najdete v tématu [postupy: určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Vzorkování  
 Tato nastavení umožňují vybrat interval vzorkování událostí a vzorkování při vzorkování se používá jako metodu profilace. Událost vzorku se používá ke shromažďování dat profilování v zadaném intervalu. Například pokud je událost vzorku hodinových cyklů a interval vzorkování je nastavený na 10 000 000 pak data profilace se shromažďují pro za každých 10 milionů hodinových cyklů. Následující čtyři typy ukázkové události jsou k dispozici:  
  
- Hodinových cyklů - procesoru vázán problémy  
  
- Problémy související s stránkování – paměť  
  
- Systém volá - pro vstupně-výstupní operace související s problémy  
  
- Čítače výkonu – problémy výkonu na nízké úrovni  
  
- Další ukázkové události lze upravit podle dostupných čítačů výkonu  
  
  Další informace najdete v tématu [jak: Zvolte událostí vzorkování](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>binární  
 Tato nastavení umožňují určit, jestli chcete přemístit instrumentované binární soubor do jiného umístění. Například pokud profilujete My.DLL a rozhodnou přemístit instrumentované binární soubor se vytvoří záložní kopie My.DLL s názvem My.Orig.DLL. Následně se mění My.DLL vložíte-li testy, shromažďovat data. Pokud se rozhodnete přemístit instrumentované binární soubor, původní binární soubor se nepřejmenuje a instrumentovaný binární soubor je zkopírován do zadaného umístění pro použití během instrumentace.  
  
 Další informace najdete v tématu [postupy: určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Interakce vrstev  
 Další informace najdete v tématu [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)  
  
## <a name="instrumentation"></a>Instrumentace  
 Tato nastavení umožňují shromažďovat údaje o výkonu pro kód JScript v [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové stránky a určete **před instrumentací** a **po instrumentaci** události, které mají být provedeny před nebo po proces instrumentace.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Profilace kódu JavaScript ve webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Postupy: Určení příkazů k provedení před instrumentací a po instrumentaci](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>Čítače CPU  
 Tato nastavení umožňují shromažďovat data o čítačích výkonu procesoru, při použití metoda profilace instrumentace. Přenosné čítače výkonu jsou k dispozici bez ohledu na využití procesoru návrhu nebo výrobce. Události platformy jsou specifické pro procesor návrhu a výrobce. Další informace o čítačích výkonu na čipu naleznete v dokumentaci pro konkrétní procesor.  
  
 Další informace najdete v tématu [postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Události Windows  
 Během profilace můžete shromažďovat data z poskytovatele trasování událostí. Data můžete zobrazit pomocí nástroje příkazového řádku VSPerfReport.exe `/calltrace` možnost. Další informace o trasování událostí pro Windows (ETW) najdete v tématu [o trasování událostí](http://go.microsoft.com/fwlink/?linkid=90752).  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Shromažďování dat Trasování událostí pro Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Čítače Windows  
 Tato možnost umožňuje shromažďovat data z čítače sledování výkonu Windows. Shromažďování těchto dat, zaškrtněte políčko s popiskem **shromažďování čítačů výkonu Windows**. Interval shromažďování lze nastavit **intervalem sběru hodnot** pole. **Kategorie čítače** a **Instance** mohou být také k dispozici. Některé výchozí čítače sledování výkonu Windows jsou k dispozici.  
  
 Další informace najdete v tématu [postupy: shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Upřesnit  
 Tato nastavení umožňují přidat možnosti do procesu instrumentace tak, že zadáte jeden nebo více možností [VSInstr](../profiling/vsinstr.md) nástroje pro profilaci příkazového řádku. Můžete také zadat verzi Common Runtime do profilu, pokud aplikace používá více než jedna verze.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Postupy: Určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)



