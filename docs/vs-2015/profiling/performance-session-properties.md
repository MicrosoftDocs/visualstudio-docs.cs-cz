---
title: Vlastnosti výkonnostní relace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af214f6a29e12dcdf2fe8bd2de75e05283894922
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74290111"
---
# <a name="performance-session-properties"></a>Vlastnosti výkonnostní relace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Výkonnostní relace** umožňuje nakonfigurovat nastavení, které určuje, jak má být aplikace profilovaná. Ukládá také sestavy, které jsou generovány pro relaci profilování.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)][!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Můžete vytvořit **relaci výkonu** spuštěním **Průvodce výkonem** nebo ručním vytvořením relace. Po vytvoření **relace výkonu** se v **prohlížeč výkonu** zobrazí **relace výkonu** .  
  
  Chcete-li zobrazit vlastnosti **relace výkonu** , vyberte název relace v **prohlížeč výkonu**, klikněte na něj pravým tlačítkem myši a vyberte možnost **vlastnosti**.  
  
  Relace výkonu má následující stránky vlastností:  
  
## <a name="general"></a>Obecné  
 Tato nastavení umožňují vybrat metodu profilace, přidat kolekci objektů rozhraní .NET a data o životnosti a zadat výchozí umístění sestavy a zásady vytváření názvů.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)  
  
 [Shromažďování dat o přidělení paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Postupy: Nastavení možností názvu souboru s údaji o výkonu](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Spustit  
 Tato nastavení umožňují vybrat ze seznamu binárních souborů a zadat pořadí spouštění binárních souborů.  
  
 Další informace najdete v tématu [Postupy: Určení binárního souboru, který se má spustit.](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Kontrol  
 Tato nastavení umožňují vybrat ukázkovou událost a interval vzorkování při použití vzorkování jako metody profilace. Ukázková událost se používá ke shromažďování dat profilování v zadaném intervalu. Například pokud je vzorová událost časová cykly a interval vzorkování je nastaven na 10 000 000, pak se data profilování shromažďují po každých 10 000 000 hodinových cyklech. K dispozici jsou tyto čtyři typy ukázkových událostí:  
  
- Hodinové cykly – pro problémy vázané na procesor  
  
- Chyby stránky – pro problémy související s pamětí  
  
- Volání systému – pro problémy související se vstupem a výstupem  
  
- Čítače výkonu – problémy s výkonem nízké úrovně  
  
- Další ukázkové události se dají zadat na základě dostupných čítačů výkonu.  
  
  Další informace najdete v tématu [Postupy: výběr událostí vzorkování.](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>Binární hodnota  
 Tato nastavení umožňují určit, zda chcete přemístit instrumentované binární soubory do jiného umístění. Pokud například vytváříte profilaci my. DLL a rozhodnete se, že nechcete přemístit instrumentované binární soubory, vytvoří se záložní kopie souboru my. DLL s názvem My. orig. DLL. Následně se my. DLL upraví vložením sond pro shromažďování dat. Pokud se rozhodnete přemístit instrumentované binární soubory, původní binární soubor se nepřejmenuje a instrumentované binární soubory se zkopírují do zadaného umístění pro použití během instrumentace.  
  
 Další informace najdete v tématu [Postupy: Určení binárního souboru, který se má spustit.](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Interakce vrstev  
 Další informace najdete v tématu [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md) .  
  
## <a name="instrumentation"></a>Instrumentace  
 Tato nastavení umožňují shromažďovat údaje o výkonu pro kód JScript na [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové stránky a určovat události **před instrumentací** a **po** instrumentaci, které chcete provést před nebo po procesu instrumentace.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Profilace kódu JavaScript ve webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Postupy: Určení příkazů k provedení před instrumentací a po instrumentaci](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>Čítače procesoru  
 Tato nastavení umožňují shromažďovat data o čítačích výkonu procesoru při použití metody profilace instrumentace. Přenosné čítače výkonu jsou k dispozici bez ohledu na návrh procesoru nebo výrobce. Události platformy jsou specifické pro návrh a výrobce procesoru. Další informace o čítačích výkonu na čipu získáte v dokumentaci ke konkrétnímu procesoru.  
  
 Další informace najdete v tématu [Postup: shromažďování dat ČÍTAČŮ procesoru.](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Události systému Windows  
 Během profilace můžete shromažďovat data z poskytovatelů trasování událostí. Data můžete zobrazit pomocí `/calltrace` možnost nástroje příkazového řádku VSPerfReport. exe. Další informace o trasování událostí pro Windows (ETW) najdete v tématu věnovaném [trasování událostí](https://go.microsoft.com/fwlink/?linkid=90752).  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Shromažďování dat Trasování událostí pro Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Čítače systému Windows  
 Tato možnost umožňuje shromažďovat data z čítačů sledování výkonu systému Windows. Chcete-li shromáždit tato data, zaškrtněte políčko s označením **shromažďovat čítače výkonu systému Windows**. Interval shromažďování dat lze nastavit v poli **interval shromažďování** . **Kategorie čítače** a **instance** mohou být také k dispozici. K dispozici jsou některé výchozí čítače sledování výkonu systému Windows.  
  
 Další informace najdete v tématu [Postup: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Upřesnit  
 Tato nastavení umožňují přidat možnosti do procesu instrumentace zadáním jedné nebo více možností nástroje pro profilaci [VSInstr](../profiling/vsinstr.md) příkazového řádku. Můžete také zadat verzi společného modulu runtime k profilaci, když aplikace používá více než jednu verzi.  
  
 Další informace naleznete v tématu:  
  
 [Postupy: Určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Postupy: Určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Viz také  
   [přehledy](../profiling/overviews-performance-tools.md)  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
