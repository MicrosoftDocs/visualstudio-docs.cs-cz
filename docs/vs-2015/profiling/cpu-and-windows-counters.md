---
title: Čítače procesoru a systému Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eceadf1b1bf82876a20027a9d29c8336e381d18d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808656"
---
# <a name="cpu-and-windows-counters"></a>Čítače procesoru a systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler sady Visual Studio umožňuje shromažďovat údaje o výkonu vygenerované operačním systémem (čítače systému Windows) a údaje o výkonu vygenerované jednotkou procesoru (čítače CPU).  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="windows-counters"></a>Čítače systému Windows  
 Čítače systému Windows jsou součástí diagnostické infrastruktury systému Windows, která poskytuje informace o výkonu operačního systému nebo aplikace, služby nebo ovladače. Čítače systému Windows závisí na konfiguraci aktuálního počítače a nemusí být k dispozici na jiných počítačích. Čítače výkonu systému Windows se shromažďují v datových souborech profilování jako značky profilace, které pak můžete použít k filtrování zobrazení a sestav.  
  
## <a name="cpu-counters"></a>Čítače procesoru  
 Čítače CPU jsou funkcí procesoru počítače, který ukládá počet událostí souvisejících s hardwarem.  Když shromáždíte data čítače procesoru pomocí metody profilace instrumentace, data se připojí k datům pro funkce a moduly. Pomocí metody instrumentace můžete shromažďovat více čítačů CPU. Při použití metody vzorkování vyberete jeden čítač, který se použije jako událost, která se má vzorkovat.  
  
 Čítače výkonu jsou specifické pro procesor. Různé modely a verze procesoru můžou mít výrazně různá nastavení konfigurace, aby se povolil stejný čítač výkonu. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Profiler přenosné události odděluje některé běžné čítače výkonu od konkrétních procesorů a umožňuje shromažďovat nebo vzorkovat Obecné události výkonu.  
  
 Pokud chcete spočítat konkrétní událost při použití profileru, například neúspěšných přístupů do mezipaměti L2, můžete vytvořit relaci výkonu kolem tohoto odesílatele události. To můžete provést na jakémkoli procesoru s mezipamětí L2. Výkonnostní relaci lze přesunout z platformy na platformu bez úprav.  
  
 Profiler sady Visual Studio nadále podporuje konkrétní události pro konkrétní platformu. Například vývojář na platformě Pentium 4 může chtít počítat události, které jsou specifické pro architekturu NetBurst. Tato událost není přenosná, ale je stále dostupná pro vývojáře pro konkrétní výkonnostní relaci na konkrétní platformě.  
  
## <a name="portable-and-platform-events"></a>Přenosné a nespravované události  
 Přenosné události představují skupinu čítačů CPU, které nejsou specifické pro konkrétní procesor. Všechny ostatní čítače CPU se nazývají události platformy a nemusí se podporovat na různých platformách.  
  
 Čítače pro přenosné i události platformy jsou definovány v. Soubory XML, kde jsou k dispozici konkrétní hodnoty, které souvisejí s čítači. Existuje více souborů pro různé procesory, protože data pro procesory Intel a AMD jsou například odlišná. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]Profiler tyto informace využívá k tomu, aby k měření výkonu prezentuje odpovídající čítače, přenosnou i platformu.  
  
### <a name="portable-events"></a>Přenosné události  
 Přenosné události obsahují následující události:  
  
 **Obecné události**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Pokyny byly vyřazeny|Určuje počet instrukcí, které se provedly, dokud se událost nedokončí.|  
|Nezastavené cykly|Označuje jenom cykly, ve kterých se procesor nezastavil, například čekání na vstupně-výstupní operace.|  
  
 **Události front-endu**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Neúspěšné ITLB|Označuje počet neúspěšných hledání ve vyrovnávací paměti pro překlad instrukcí, které vedlo k neúspěšnému zjištění.|  
  
 **Události větve**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Vyřazené větve|Označuje počet instrukcí větve, které se provedly, dokud se událost nedokončí.|  
|Nepředvídatelné větve|Označuje nepředvídatelné větve, ke kterým dochází, protože procesor předpovídá nesprávnou cestu. Nepředvídatelné větve mají vliv na výkon, protože procesor musí zrušit veškerou práci a znovu ji spustit na správné cestě.|  
  
 **Události paměti:**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Neúspěšné čtení z mezipaměti L2|Označuje počet neúspěšných přístupů ke čtení mezipaměti druhé úrovně.|  
|Odkazy čtení mezipaměti L2|Označuje počet odkazů na čtení mezipaměti druhé úrovně. Zahrnuje Neúspěšné přístupy do zatížení a čtení z důvodů přístupů a přístupů do vlastnictví (RFO).|  
  
## <a name="viewing-available-counters"></a>Zobrazení dostupných čítačů  
 Dostupné čítače procesoru v integrovaném vývojovém prostředí sady Visual Studio můžete zobrazit v okně příkazového řádku.  
  
### <a name="visual-studio-ui"></a>Uživatelské rozhraní sady Visual Studio  
 Chcete-li zobrazit seznam dostupných čítačů v počítači v integrovaném vývojovém prostředí sady Visual Studio, je nutné mít v Prohlížeč výkonu otevřenu relaci výkonu profileru.  
  
##### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Zobrazení seznamu všech čítačů CPU podporovaných aktuální platformou  
  
1. V Prohlížeč výkonu klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.  
  
2. Proveďte jednu z následujících akcí:  
  
   - Klikněte na **vzorkování**a potom v seznamu **vzorových** událostí vyberte **čítač výkonu** . Čítače CPU jsou uvedeny v části **Dostupné čítače výkonu**.  
  
      **Poznámka:** Kliknutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci vzorkování.  
  
     -nebo-  
  
   - Vyberte **čítače procesoru**a pak vyberte **shromáždit čítače procesoru**. Čítače CPU jsou uvedeny v části **Dostupné čítače**.  
  
      **Poznámka:** Kliknutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci shromažďování čítačů.  
  
##### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Zobrazení seznamu čítačů oken, které jsou podporovány na aktuální platformě  
  
1. V Prohlížeč výkonu klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.  
  
2. Klikněte na **čítače systému Windows**.  
  
3. Vyberte možnost **shromáždit čítače systému Windows**.  
  
4. V seznamu **kategorie čítače** vyberte skupinu čítačů. V seznamu se zobrazí čítač Windows pro skupinu.  
  
     **Poznámka:** Kliknutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci shromažďování čítačů.  
  
### <a name="command-line"></a>Příkazový řádek  
 Pomocí nástroje příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) můžete zobrazit seznam čítačů CPU, které jsou k dispozici v počítači z příkazového řádku.  
  
##### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Seznam čítačů PROCESORů, které jsou podporovány na aktuální platformě  
  
1. Otevřete okno příkazového řádku.  
  
2. Typ  
  
     **\<Visual Studio Performance Tools Directory>\VSPerfCmd/QueryCounters**  
  
     kde **\<Visual Studio Performance Tools Directory>** je cesta k adresáři nástrojů pro sledování výkonu instalace sady Visual Studio, obvykle  
  
     C:\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)   
 [Postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)   
 [Postupy: Shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md)
