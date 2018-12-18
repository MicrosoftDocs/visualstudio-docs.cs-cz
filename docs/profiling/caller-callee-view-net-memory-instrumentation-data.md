---
title: Zobrazení volající volaný – Data instrumentace paměti NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6005bfcd4c69220c26929a8ad57f0e37923f388c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265498"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Zobrazení volající/volaný – instrumentace paměti .NET Data
Zobrazení volající/volaný paměti .NET profilace data, která nebyla shromážděna pomocí metody instrumentace zobrazí přidělení a dat časování pro vybrané funkce a funkce nadřazených a podřízených jeho vybrané funkce. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Funkci Current** se zobrazí v mřížce střední a zobrazuje informace o vybrané funkce profilace sledováním využívání paměti. Hodnoty zahrnují u všech vybraných volání funkce.  
  
 **Funkce, které volá funkci current** se zobrazí v horní mřížky, a zobrazuje množství hodnotu vybrané (aktuální) funkce, který byl vygenerován volání z funkce volající (nadřazené).  
  
 **Funkce, které byly volá funkci current** se zobrazí v mřížce dole, a zobrazuje paměti při volání funkce podřízené aktuální funkcí profilace data pro funkce volaný (podřízená) vybrané funkce.  
  
 Dvakrát klikněte na volající nebo volaný funkce řádek, aby který řádek aktuální funkce.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání této funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu profilace spustit.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Režijní náklady na čas výhradní testu**|Čas režie pro tuto funkci z důvodu instrumentace. Režijní náklady na test odečtení od sebe výhradní.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci a jeho podřízené funkce z důvodu instrumentace. Test režie odečtení od sebe (včetně).|  
|**Typ**|Kontext funkce:<br /><br /> **0** -aktuální funkce<br /><br /> **1** -funkci, která volá funkci current<br /><br /> **2** -funkci, která volá funkci current<br /><br /> Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Název kořenové – funkce**|Název aktuální funkce. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="net-memory-allocation-values"></a>Hodnoty přidělení paměti .NET  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní přidělení**|-Pro funkci aktuální počet objektů, které byly vytvořeny při funkce provádění kódu v těle funkce (to znamená, když funkce se v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volat pomocí této funkce.<br />-Pro volající funkce počet výhradní přidělení aktuální funkce, které byly vygenerovány volání z této funkce volajícího.<br />-Pro funkci volaný, počet objektů, které byly vytvořeny instance této funkce, které byly volá funkci aktuální. Toto číslo nezahrnuje objekty, které byly vytvořené pomocí funkce, které byly volá funkci volaný.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly výhradní přidělení této funkce.|  
|**Přidělení (včetně).**|-Pro aktuální funkci Počet objektů, které byly přiděleny funkcí v profilaci spustit. Počet zahrnuje objekty, které byly vytvořeny v volaný funkce, které byly volá funkci.<br />-Pro volající funkce počet včetně přidělení aktuální funkce, které byly vygenerovány volání z této funkce volajícího.<br />-Pro funkci volaný, počet objektů, které byly přiděleny instancí této funkce, které byly vygenerovány volání z aktuální funkce. Počet zahrnuje provedené funkce, které byly volat pomocí této funkce volaný přidělení.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní bajtů**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny funkcí v profilaci spustit. Číslo nezahrnuje pamětí přidělenou volaný funkcí, které byly volá funkci.<br />-Pro volající funkci Počet výhradní bajtů aktuální funkce, které byly generovány od volá pomocí této funkce volajícího.<br />-Pro funkci volaný, počet bajtů, které byly přiděleny instancí této funkce, které byly vygenerovány volání z aktuální funkce. Počet bajtů, které byly přiděleny podle funkce, které byly volá funkci volaný neobsahuje.|  
|**% Výhradní bajtů**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly výhradní přidělení této funkce.|  
|**Bajtů (včetně).**|-Pro aktuální funkci Počet bajtů v paměti, které byly přiděleny funkcí v profilaci spustit. Počet zahrnuje pamětí přidělenou volaný funkcí, které byly volá funkci.<br />-Pro volající funkce počet včetně bajtů instancí aktuální funkce, které byly vygenerovány volání z této funkce volajícího.<br />-Pro funkci volaný, počet bajtů, které byly přiděleny instancí této funkce, které byly vygenerovány volání z aktuální funkce. Obsahuje počet bajtů, které byly přiděleny podle funkce, které byly volat pomocí této funkce volaný.|  
|**% Bajtů (včetně).**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly včetně přidělení této funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas zahrnuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|-Pro aktuální funkci času stráveného ve funkci. Hodnota obsahuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce časového intervalu uplynulá včetně aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkci volaný času stráveného v této funkce, který byl vygenerován volá z aktuální funkce. Hodnota obsahuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**% Uplynulá doba (včetně).**|Procento celkového počtu uplynulý čas včetně času stráveného v uplynulé době (včetně). Tato funkce v tomto kontextu spuštění profilování.|  
|**Průměr uplynulý čas včetně čas**|Průměr uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba (včetně).**|Maximální uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Min uplynulý čas včetně čas**|Minimální uplynulý čas včetně volání této funkce v tomto kontextu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve voláních operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|-Pro aktuální funkci času stráveného při provádění tělo funkce. Hodnota vyloučí dobu, po kterou byl stráven v podřízené funkce, ale zahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce časového intervalu uplynulá výhradní aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkci volaný času stráveného v této funkce, který byl vygenerován volá z aktuální funkce. Hodnota vyloučí dobu, po kterou byl stráven v podřízené funkce volaný funkce, ale zahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Uplynulý čas výhradní %**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven v celková doba uplynulá výhradní této funkce v tomto kontextu.|  
|**Průměr uplynulý exkluzivní čas**|Průměr uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba výhradní**|Maximální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Min uplynulý exkluzivní čas**|Minimální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|-Pro aktuální funkci času stráveného v funkce a jeho podřízené funkce. Hodnota vyloučí času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce, včetně dobu aplikace aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkce volaný času stráveného v tato funkce a jeho podřízené funkce, který byl vygenerován volání z aktuální funkce. Hodnota nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Aplikace % času (včetně).**|Procento uplynulé době celkový včetně profilace spuštění, který byl stráven v čase celkový aplikace (včetně). Tato funkce v tomto kontextu.|  
|**Prům. čas včetně aplikace**|Průměrná aplikace čas včetně volání této funkce v tomto kontextu.|  
|**Maximální doba včetně aplikace**|Čas (včetně). maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba včetně aplikace min.**|Čas včetně minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty aplikace znamenat času stráveného ve funkci, s výjimkou času stráveného v podřízené funkce. Uvedené čas vyloučí také dobu, po kterou byl strávený incalls operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|-Pro aktuální funkci času stráveného při provádění tělo funkce. Hodnota nezahrnuje času stráveného v podřízené funkce ani nezahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce množství času výhradní aplikace aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkci volaný času stráveného v této funkce, který byl vygenerován volá z aktuální funkce. Hodnota nezahrnuje času stráveného v podřízené funkce funkce volaný ani nezahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Aplikace % výhradní čas**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven výhradní včas celkový aplikace této funkce v tomto kontextu.|  
|**Prům. čas výhradní aplikace**|Průměrná aplikace čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální doba výhradní aplikace**|Čas výhradní maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba výhradní aplikace min.**|Čas výhradní minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení volající/volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)   
 [Zobrazení volající/volaný – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)