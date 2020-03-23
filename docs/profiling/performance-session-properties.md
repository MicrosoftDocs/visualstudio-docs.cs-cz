---
title: Vlastnosti relace výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772199"
---
# <a name="performance-session-properties"></a>Vlastnosti výkonnostní relace

**Relace výkonu** umožňuje konfigurovat nastavení, která určují, jak je aplikace profilována. Ukládá také sestavy, které jsou generovány pro relaci profilování.

Relaci **výkonu** vytvoříte spuštěním **Průvodce výkonem** nebo ručním vytvořením relace. **Relace výkonu** se zobrazí v **Průzkumníku výkonu** po vytvoření relace **výkonu.**

Chcete-li zobrazit vlastnosti **relace výkonu,** vyberte název relace v **Průzkumníku výkonu**, klepněte na něj pravým tlačítkem myši a vyberte příkaz **Vlastnosti**.

Relace výkonu má následující stránky vlastností:

## <a name="general"></a>Obecné

Tato nastavení umožňují vybrat metodu profilování, přidat data o kolekci objektů .NET a data životnosti a určit výchozí umístění sestavy a konvence pojmenování.

Další informace naleznete v tématu:

[Postup: Zvolte metody kolekce](../profiling/how-to-choose-collection-methods.md)

[Shromažďování dat o alokaci paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Postupy: Nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Spuštění

Tato nastavení umožňují vybrat ze seznamu binárních souborů a určit počáteční pořadí binárních souborů.

Další informace naleznete v [tématu How to: Specify the binary to start](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Vzorkování

Tato nastavení umožňují vybrat vzorkovací událost a interval vzorkování při použití vzorkování jako metoda profilování. Ukázková událost se používá ke shromažďování dat profilování v zadaném intervalu. Například pokud ukázková událost je hodiny cykly a interval vzorkování je nastavena na 10 000 000 pak profilování data jsou shromažďovány po každých 10 milionů cyklů hodin. K dispozici jsou následující čtyři typy ukázkových událostí:

- Clock Cycles - pro problémy vázané na CPU
- Chyby stránky - pro problémy související s pamětí
- Systémové výzvy - pro i/o související problémy
- Čítače výkonu – pro problémy s výkonem na nízké úrovni
- Další ukázkové události lze zadat na základě dostupných čítačů výkonu.

Další informace naleznete v [tématu How to: Choose sampling events](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>binární
Tato nastavení umožňují určit, zda chcete přemístit instrumentovaný binární soubor do jiného umístění. Pokud například profilujete službu *My.DLL* a rozhodnete se instrumentovaný binární soubor nepřemístit, vytvoří se záložní kopie služby *My.DLL* s názvem *My.Orig.DLL.* Následně *My.DLL* je upraven vložením sond ke shromažďování dat. Pokud se rozhodnete přemístit instrumentovaný binární soubor, původní binární není přejmenován a instrumentovaný binární soubor je zkopírován do zadaného umístění pro použití během instrumentace.

Další informace naleznete v [tématu How to: Specify the binary to start](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Interakce s úrovní

Další informace naleznete v [tématu Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>Instrumentace

Tato nastavení umožňují shromažďovat údaje o výkonu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kódu JScript na webových stránkách a určit všechny události **před nástrojem** a **po instrumentaci,** ke kterým chcete dojít před nebo po procesu instrumentace.

Další informace naleznete v tématu:

[Postup: Profil javascriptového kódu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Postup: Určení příkazů před a po přístroji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>Čítače procesoru

Tato nastavení umožňují shromažďovat data o čítačích výkonu procesoru při použití metody profilování instrumentace. Přenosné čítače výkonu jsou k dispozici bez ohledu na návrh procesoru nebo výrobce. Události platformy jsou specifické pro návrh procesoru a výrobce. Další informace o čítačích výkonu na čipu naleznete v dokumentaci k konkrétnímu procesoru.

Další informace naleznete v [tématu How to: Collect CPU counter data](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Události systému Windows

Během profilování můžete shromažďovat data od zprostředkovatelů trasování událostí. Data můžete zobrazit pomocí volby nástroje `/calltrace` příkazového řádku *VSPerfReport.exe.* Další informace o trasování událostí pro Windows (ETW) naleznete v [tématu O trasování událostí](/windows/win32/etw/about-event-tracing).

Další informace naleznete v tématu:

[Postup: Shromažďování trasování událostí pro windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Čítače Systému Windows

Tato možnost umožňuje shromažďovat data z čítačů sledování výkonu systému Windows. Chcete-li tato data shromažďovat, zaškrtněte políčko **Shromáždit čítače výkonu systému Windows**. Interval kolekce lze nastavit v poli **Interval kolekce.** **Kategorie čítače** a **instance** mohou být také k dispozici. K dispozici jsou některé výchozí čítače sledování výkonu systému Windows.

 Další informace naleznete v [tématu How to: Collect Windows counter data](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Upřesňující

Tato nastavení umožňují přidat možnosti do procesu instrumentace zadáním jedné nebo více možností nástroje profilování příkazového řádku [VSInstr.](../profiling/vsinstr.md) Můžete také určit verzi Common Runtime profilu, pokud aplikace používá více než jednu verzi.

Další informace naleznete v tématu:

[Postupy: Určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Postupy: Určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md)
[Konfigurace relací](../profiling/configuring-performance-sessions.md)
výkonu[Řízení shromažďování dat](../profiling/controlling-data-collection.md)
