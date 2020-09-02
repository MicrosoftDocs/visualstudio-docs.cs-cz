---
title: Přehled sestavy výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd8732a914581b39566bac88fe73698850893f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785049"
---
# <a name="performance-report-overview"></a>Přehled sestav výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data profilování relace výkonu můžete zobrazit v okně **Sestava výkonu** v integrovaném vývojovém prostředí (IDE) sady Visual Studio Team System Development Edition. Data profilování se ukládají do souborů. vsp a. vsps. Okna zobrazení sestav umožňují zobrazit a analyzovat problémy s výkonem aplikací.  
  
> [!CAUTION]
> Soubor dat profilování obsahuje citlivé informace, jako je název počítače, verze operačního systému, cesty k souborům, informace o paměti a další informace o nastavení počítače. Měli byste udržovat přísnou kontrolu nad distribucí dat, jak v nativním formátu. VSP, tak při exportu do souboru. csv nebo souboru. XML.  
>   
> Pokud se data trasování událostí shromažďují jako součást relace výkonu, můžou se v souboru protokolu trasování událostí (. ETL) zobrazit další informace. Tyto informace zahrnují vaši doménu a uživatelské jméno; Proto byste měli udržovat přísnou kontrolu nad distribucí souboru protokolu.  
  
## <a name="performance-report-window"></a>Okno sestavy výkonu  
 Okno Sestava výkonu je okno nástroje, které slouží k zobrazení, správě a filtrování údajů o výkonu a obsahuje přizpůsobitelný ovládací prvek dotazu.  
  
 Na hlavním panelu nástrojů okna Sestava výkonu můžete získat přístup ke každému zobrazení. Kliknutím na šipku vedle seznamu **aktuální zobrazení** zobrazíte a vyberete jednotlivá zobrazení, která jsou k dispozici.  
  
 Okno Sestava výkonu poskytuje následující zobrazení dat:  
  
### <a name="summary-view"></a>Souhrnné zobrazení  
 Ve výchozím nastavení se data profilování zobrazují v souhrnném zobrazení. Toto zobrazení je výchozí bod v šetření týkající se problémů s výkonem. Z každého řádku v souhrnném zobrazení můžete přejít na podrobnější zobrazení tak, že kliknete pravým tlačítkem myši na název funkce nebo modulu. Další informace najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Zobrazení olající/volaný  
 Zobrazení volající/volaný zobrazí strom volání pro jednotlivé funkce. Zobrazení je rozdělené na tři části:  
  
- Funkce Target se zobrazuje uprostřed zobrazení.  
  
- Funkce, které volaly funkci (volající), se zobrazí nad cílovou funkcí.  
  
- Funkce, které jsou volány cílovou funkcí (volané), jsou zobrazeny pod cílem.  
  
  Jinou funkci můžete vybrat tak, že dvakrát kliknete na libovolnou funkci v seznamu volané nebo na seznam volaný. Další informace naleznete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Zobrazení stromu volání  
 Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které zavolaly, a údaje o výkonu pro tato volání funkcí.  
  
 Zobrazení stromu volání může také rozšiřovat a zvýrazňovat cestu spuštění funkce, která využila nejvíce času nebo byla Navzorkovaná častěji. Pokud chcete zobrazit nejvíce aktivních cest, klikněte na ni pravým tlačítkem myši a pak klikněte na Rozbalit kritickou **cestu**. Další informace naleznete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Zobrazení procesů  
 Zobrazení procesu zobrazuje údaje o výkonu pro každý proces a podproces, který byl profilace. Další informace najdete v tématu [zobrazení procesu](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Zobrazení modulů  
 Moduly zobrazí seznam modulů v projektu a prezentují data profilování pro každý modul. Rozbalte nebo sbalte název modulu, aby se zobrazila data profilace funkce. Když byla data shromážděna pomocí vzorkování, jsou k dispozici také data profilace a ukazatele pokynů pro zdrojový kód. Další informace najdete v tématu [zobrazení modulů](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Zobrazení funkcí  
 Zobrazení funkcí obsahuje seznam funkcí, které byly volány během profilace. Další informace najdete v tématu [zobrazení funkcí](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Řádkové zobrazení  
 Zobrazení řádků umožňuje zobrazit konkrétní řádky zdrojového kódu, které byly provedeny během profilace vzorkování. Další informace najdete v tématu [zobrazení řádků](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Zobrazení ukazatele na instrukce (IP)  
 Zobrazení ukazatele na instrukce vám umožní zobrazit konkrétní pokyny, které byly provedeny během profilace vzorkování. Další informace najdete v tématu [zobrazení ukazatelů na instrukce (IP)](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Zobrazení přidělení  
 Zobrazení přidělení je k dispozici v případě, že je na stránce **Obecné** v dialogovém okně vlastnosti **relace výkonu** vybráno **shromažďování objektů .NET** . Viz [Přehled relace výkonu](../profiling/performance-session-overview.md). Zobrazení přidělení uvádí seznam objektů rozhraní .NET, které byly přiděleny aplikací nebo komponentou. Po rozbalení řádku objektu se zobrazí strom volání. Strom volání zobrazuje cesty spuštění, které vedly k vytvoření objektu. Zobrazí se také informace o počtu zahrnutých a exkluzivních přidělení pro každou funkci ve stromu volání. Zobrazení přidělení může také rozšiřovat a zvýrazňovat cestu spuštění funkce, která přidělila nejvyšší počet objektů. Pokud chcete zobrazit nejvíce aktivních cest, klikněte na ni pravým tlačítkem myši a pak klikněte na Rozbalit kritickou **cestu**. Další informace najdete v tématu [shromažďování dat o přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Zobrazení doby života objektů  
 Zobrazení životnosti objektů je k dispozici v případě, že jsou na stránce **Obecné** v dialogovém okně vlastnosti **výkonnostní relace** vybrány informace o **přidělení objektů** .NET a **také informace o době života objektu .NET** .  
  
 Zobrazení životnosti objektů zobrazuje celkový počet instancí každého typu a počet objektů, které byly shromážděny při každé generaci uvolňování paměti. Další informace najdete v tématu [zobrazení životnosti objektu](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Přizpůsobitelný ovládací prvek filtru  
 Přizpůsobitelný ovládací prvek filtru má následující možnosti:  
  
- **Filtr importu** – načte dříve uložený vlastní dotaz.  
  
- **Exportovat filtr** – uloží vlastní dotaz do zadaného umístění.  
  
- **Spustit dotaz** – spustí dotaz, jak je zobrazen v ovládacím prvku Custom Query.  
  
- **Zastavit dotaz** – zastaví provádění dotazu, na kterém je spuštěný. Toto tlačítko není k dispozici, pokud žádný dotaz neběží.  
  
- **Zobrazit dotaz** – zobrazí nebo skryje ovládací prvek vlastní dotaz.  
  
- **Uložit analyzované** – uloží sestavu spolu se svou aktuální analýzou jako soubor. vsps.  
  
- **Export** – uloží aktuální sestavu v. CVS – formátování nebo. Soubor ve formátu XML s možnostmi pro uložení různých zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Analýza dat nástrojů výkonu](../profiling/analyzing-performance-tools-data.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
