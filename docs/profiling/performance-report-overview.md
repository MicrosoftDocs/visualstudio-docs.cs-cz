---
title: Přehled zprávy o výkonnosti | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 517156677a6d3711fa5dc2e4a15629a55229cfe2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772229"
---
# <a name="performance-report-overview"></a>Přehled zprávy o výkonu
Data profilování relace výkonu můžete zobrazit v okně **Sestava výkonu** integrovaného vývojového prostředí (IDE) sady Visual Studio Team System Development Edition. Data profilování jsou uložena v souborech .vsp a .vsps. Okna zobrazení sestavy umožňují zobrazit a analyzovat problémy s výkonem aplikace.

> [!CAUTION]
> Datový soubor profilování obsahuje citlivé informace, jako je název počítače, verze operačního systému, cesty k souborům, informace o paměti a další informace o nastavení počítače. Měli byste udržovat přísnou kontrolu nad distribucí dat, a to jak v nativním . *vsp* a při exportu do . *csv* nebo . *xml.*
>
> Pokud jsou data trasování událostí shromažďována v rámci relace výkonu, mohou se v protokolu trasování událostí (.* etl*) souboru. Tyto informace zahrnují vaši doménu a uživatelské jméno. Proto byste měli udržovat přísnou kontrolu nad distribucí souboru protokolu.

## <a name="performance-report-window"></a>Okno Zpráva o výkonu
 Okno Sestava výkonu je okno nástroje, které slouží k zobrazení, správě a filtrování dat o výkonu a obsahuje přizpůsobitelný ovládací prvek dotazu.

 Na hlavním panelu nástrojů okna Zpráva o výkonu můžete přistupovat ke každému zobrazení. Kliknutím na šipku vedle seznamu **Aktuální zobrazení** zobrazíte a vyberte jednotlivá dostupná zobrazení.

 Okno Sestava výkonu poskytuje následující zobrazení dat:

### <a name="summary-view"></a>Souhrnné zobrazení
 Ve výchozím nastavení se data profilování zobrazují v souhrnném zobrazení. Toto zobrazení je výchozím bodem při vyšetřování problémů s výkonem. Z každého řádku v souhrnném zobrazení můžete přejít na podrobnější zobrazení kliknutím pravým tlačítkem myši na funkci nebo název modulu. Další informace naleznete v [tématu Souhrnné zobrazení](../profiling/summary-view.md).

### <a name="callercallee-view"></a>Zobrazení olající/volaný
 Zobrazení Volající/Volaný zobrazuje strom volání pro jednotlivé funkce. Pohled je rozdělen do tří částí:

- Cílová funkce se zobrazí uprostřed pohledu.

- Funkce, které volaly funkci (volající) jsou zobrazeny nad cílovou funkcí.

- Funkce, které jsou volány cílovou funkcí (volané) jsou zobrazeny pod cílem.

  Můžete vybrat jinou funkci poklepáním na libovolnou funkci v volaném seznamu nebo seznamu volaných. Další informace naleznete v [tématu Caller/Callee View](../profiling/caller-callee-view.md).

### <a name="call-tree-view"></a>Zobrazení stromu volání
 Zobrazení Strom volání zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupníbod do aplikace nebo součásti. Každý uzel funkce uvádí všechny funkce, které volal a údaje o výkonu těchto volání funkce.

 Strom volání zobrazení můžete také rozbalit a zvýraznit cestu spuštění funkce, která spotřebovává nejvíce času nebo byl vzorkován nejčastěji. Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**. Další informace naleznete v tématu [Zobrazení stromu volání](../profiling/call-tree-view.md).

### <a name="process-view"></a>Zobrazení procesů
 Zobrazení Proces zobrazuje údaje o výkonu pro každý proces a vlákno, které bylo profilováno. Další informace naleznete v [tématu Process View](../profiling/process-view.md).

### <a name="modules-view"></a>Zobrazení modulů
 Zobrazení Moduly uvádí moduly v projektu a představuje data profilování pro každý modul. Rozbalte nebo sbalte název modulu, aby se zobrazila data profilování funkcí. Když byla data shromážděna pomocí vzorkování, řádek zdrojového kódu a data profilování ukazatele instrukce jsou také k dispozici. Další informace naleznete v [tématu Modules View](../profiling/modules-view.md).

### <a name="functions-view"></a>Zobrazení funkcí
 Funkce zobrazení uvádí funkce, které byly volány během profilování. Další informace naleznete v tématu [Functions View](../profiling/functions-view.md).

### <a name="line-view"></a>Zobrazení čáry
 Zobrazení Řádky umožňuje zobrazit konkrétní řádky zdrojového kódu, které byly provedeny během profilování vzorkování. Další informace naleznete v [tématu Zobrazení řádků](../profiling/lines-view.md).

### <a name="instruction-pointer-ip-view"></a>Zobrazení ukazatele instrukcí (IP)
 Zobrazení ukazatel instrukce umožňuje zobrazit konkrétní pokyny, které byly provedeny během vzorkování profilování. Další informace naleznete v [tématu Ininstruction Pointers (IP) View](../profiling/instruction-pointers-ips-view.md).

### <a name="allocation-view"></a>Zobrazení přidělení
 Zobrazení přidělení je k dispozici, pokud bylo na stránce **Obecné** v dialogovém okně **Vlastnosti relace výkonu** **vybráno shromáždit přidělení objektů .NET.** Viz [Přehled relace výkonu](../profiling/performance-session-overview.md). Zobrazení Přidělení obsahuje seznam objektů .NET, které byly přiděleny aplikací nebo komponentou. Při rozbalení řádku objektu se zobrazí strom volání. Strom volání zobrazuje cesty spuštění, které vedly k vytvoření objektu. Zobrazí se také informace o počtu včetně a výhradní přidělení pro každou funkci ve stromu volání. Zobrazení přidělení můžete také rozbalit a zvýraznit cestu spuštění funkce, která přidělila největší počet objektů. Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**. Další informace naleznete v [tématu Shromažďování přidělení paměti .NET a data životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).

### <a name="objects-lifetime-view"></a>Zobrazení životnosti objektů
 Zobrazení Životnost objektu je k dispozici, pokud byly na stránce **Obecné** dialogového okna **Vlastnosti relace výkonu** vybrány informace o shromažďování informací o **přidělení objektu .NET** a **také shromažďování informací o životnosti objektu .NET.**

 Zobrazení Životnost objektu zobrazuje celkový počet instancí každého typu a počet objektů, které byly shromážděny v každé generaci uvolňování paměti. Další informace naleznete v [tématu Zobrazení životnosti objektu](../profiling/object-lifetime-view.md).

## <a name="customizable-filter-control"></a>Přizpůsobitelný ovládací prvek filtru
 Přizpůsobitelný ovládací prvek filtru má následující možnosti:

- **Importovat filtr** - načte dříve uložený vlastní dotaz.

- **Exportní filtr** - uloží vlastní dotaz do zadaného umístění.

- **Spustit dotaz** - spustí dotaz tak, jak je zobrazen ve vlastním ovládacím prvku dotazu.

- **Zastavit dotaz** - zastaví provádění dotazu, který je spuštěn. Toto tlačítko není k dispozici, pokud není spuštěn žádný dotaz.

- **Zobrazit dotaz** - zobrazí/skryje vlastní ovládací prvek dotazu.

- **Uložit analyzed** - uloží sestavu spolu s její aktuální analýzou jako soubor .vsps.

- **Export** - uloží aktuální sestavu do . CVS ve formátu nebo . XML formátovaný soubor s možnostmi uložení různých zobrazení.

## <a name="see-also"></a>Viz také
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
- [Zobrazení sestavy výkonu](../profiling/performance-report-views.md)
