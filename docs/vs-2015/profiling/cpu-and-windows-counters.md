---
title: Windows čítače procesoru a | Dokumentace Microsoftu
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
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f79eeae8539657f6556b87d917f991113c5de807
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801690"
---
# <a name="cpu-and-windows-counters"></a>Čítače procesoru a systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profiler umožňuje shromažďovat data o výkonu, který byl vygenerován v operačním systému (Windows čítače) a data výkonu, která byla vygenerována procesor (čítače CPU).  
  
 **Požadavky**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="windows-counters"></a>Čítače Windows  
 Čítače Windows jsou součástí infrastruktury diagnostiky Windows, který poskytuje informace o výkonu operačního systému nebo aplikace, služby nebo ovladače. Čítače Windows závisí na konfiguraci počítače aktuální a nemusí být k dispozici na jiných počítačích. Čítače výkonu Windows jsou shromážděny v Profilování datové soubory jako profilovací značky, které lze použít k filtrování zobrazení a sestavy.  
  
## <a name="cpu-counters"></a>Čítače CPU  
 Čítače CPU jsou funkce procesoru počítače, ve kterém uložený počet událostí související s hardwarem.  Při shromažďování dat čítačů procesoru pomocí metoda profilace instrumentace, data se připojí k datům pro funkce a moduly. Můžete shromažďovat více čítačů procesoru pomocí metody instrumentace. Při použití metody vzorkování je vybrat jeden čítač používat jako událost se odeberou.  
  
 Čítače výkonu jsou specifické pro procesor. Různé modely a verzích Procesorem může mít výrazně odlišné konfigurace nastavení pro povolení stejnému čítači výkonu. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Události přenositelnosti Profiler oddělit pár běžných čítačů výkonu z konkrétní procesory a vám umožní shromažďovat nebo ukázkový události obecného výkonu.  
  
 Pokud budete chtít zjistit konkrétní události při použití profileru, například výpadky mezipaměti L2, můžete vytvořit relaci výkonu kolem tohoto odesílatele události. To lze provést v libovolném procesoru pomocí mezipaměti L2. Relace výkonu je možné přesunout z platformách bez úprav.  
  
 Profiler sady Visual Studio i nadále podporuje určité události pro konkrétní platformu. Například pro vývojáře na platformě Pentium 4, může být vhodné k počítání událostí, které jsou specifické pro architekturu NetBurst. Tato událost není přenosné, ale stále k dispozici pro vývojáře pro relaci výkonu specifické pro konkrétní platformy.  
  
## <a name="portable-and-platform-events"></a>Přenosné a události platformy  
 Události přenositelnosti jsou skupiny čítače CPU, které nejsou specifické pro konkrétní procesor. Další čítače CPU se nazývají událostí platformy a nemusí být podporován na různých platformách.  
  
 Čítače pro platformy i přenosné události jsou definovány v. Soubory XML, kde jsou k dispozici konkrétní hodnoty, které se vztahují na čítače. Existuje více souborů pro různé procesory, protože data pro Intel a procesory AMD, například se liší. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Profiler používá tyto informace k dispozici odpovídající čítače, přenosné a platformě, uživatelům pro měření výkonu.  
  
### <a name="portable-events"></a>Události přenositelnosti  
 Události přenositelnosti obsahovat následující události:  
  
 **Obecné události**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Instrukce|Označuje počet pokyny, které udělat, dokud dokončení události.|  
|Nezastavené cykly|Označuje pouze cykly, ve kterých procesoru není zastavená, například čekání na vstupně-výstupních operací.|  
  
 **Přední události**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Výpadky ITLB|Označuje počet vyhledávání instrukce překlad doplňování vzhled vyrovnávací paměti, jejichž výsledkem by chyběla.|  
  
 **Události větvě**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|Provedené větve|Označuje počet větvicí instrukce udělat, dokud dokončení události.|  
|Nepředpovězené větve|Označuje nepředpovězené větve, ke kterým dochází, protože procesor předpovědět nesprávné cesty. Nepředpovězené větve ovlivnit výkon, protože procesor musí zrušit veškerou práci prováděnou a znovu ji spusťte na správnou cestu.|  
  
 **Události paměti:**  
  
|Název události|Popis události|  
|----------------|-----------------------|  
|L2 Výpadky čtení mezipaměti|Označuje, že počet druhý mezipaměť na úrovni čtení výpadky.|  
|L2 Odkazy čtení mezipaměti|Označuje, že počet druhý mezipaměť na úrovni čtení odkazy. Zahrnuje výpadky načtení a čtení pro Neúspěšné přístupy do vlastnictví (předpisy RRO) a počet přístupů.|  
  
## <a name="viewing-available-counters"></a>Zobrazení dostupné čítače  
 V okně příkazového řádku, můžete vytvořit seznam na dostupné čítače CPU v integrovaném vývojovém prostředí sady Visual Studio.  
  
### <a name="visual-studio-ui"></a>Uživatelské rozhraní sady Visual Studio  
 Seznam dostupných čítačů na počítač v integrovaném vývojovém prostředí sady Visual Studio, musí mít relaci profileru výkonu, otevřete v prohlížeči výkonu.  
  
##### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Chcete-li zobrazit seznam seznam všech čítačů využití procesoru, které jsou podporovány na aktuální platformě  
  
1. V prohlížeči výkonu, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2. Proveďte jednu z těchto akcí:  
  
   - Klikněte na tlačítko **vzorkování**a pak vyberte **čítač výkonu** z **ukázka** seznamu událostí. Čítače CPU jsou uvedeny v **dostupných čítačů výkonu**.  
  
      **Poznámka:** klikněte na tlačítko **zrušit** vrátit k předchozí konfiguraci odběru vzorků.  
  
     -nebo-  
  
   - Vyberte **čítače CPU**a pak vyberte **shromáždit čítače CPU**. Čítače CPU jsou uvedeny v **dostupné čítače**.  
  
      **Poznámka:** klikněte na tlačítko **zrušit** vrátit k předchozí konfiguraci kolekce čítačů.  
  
##### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Chcete-li zobrazit seznam seznam čítačů okno, které jsou podporovány na aktuální platformě  
  
1.  V prohlížeči výkonu, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **čítače Windows**.  
  
3.  Vyberte **shromáždit čítače Windows**.  
  
4.  Z **kategorie čítače** vyberte čítačů skupiny. Čítače Windows pro skupiny se zobrazí v seznamu.  
  
     **Poznámka:** klikněte na tlačítko **zrušit** vrátit k předchozí konfiguraci kolekce čítačů.  
  
### <a name="command-line"></a>Příkazový řádek  
 Použití [VSPerfCmd](../profiling/vsperfcmd.md) nástroj příkazového řádku, můžete vytvořit seznam čítačů využití procesoru, které jsou dostupné v počítači z příkazového řádku.  
  
##### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Do seznamu čítače CPU, které jsou podporované na aktuální platformě  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Typ  
  
     **\<Visual Studio výkonu nástroje adresář >/querycounters \VSPerfCmd**  
  
     kde  **\<adresář nástrojů výkonu služby Visual Studio >** obvykle představuje cestu k adresáři nástroje pro měření výkonu instalaci sady Visual Studio  
  
     C:\Program Files\Microsoft Visual Studio 10.0\Team nástroje nástroje  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)   
 [Postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)   
 [Postupy: Shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md)



