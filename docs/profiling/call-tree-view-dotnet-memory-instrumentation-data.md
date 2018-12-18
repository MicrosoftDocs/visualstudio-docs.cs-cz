---
title: Zobrazení stromu volání – Data instrumentace paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05286c10758c19f1e3f5a5692f814a096763544
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263595"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Zobrazení stromu volání – data instrumentace paměti .NET
Zobrazení stromu volání .NET paměti přidělení profilování dat, která nebyla shromážděna pomocí metody instrumentace zobrazuje cesty provádění funkce, které byly provázán v PROFILOVANÉHO aplikaci. Kořen stromu je vstupním bodem do aplikací nebo součástí. Každý uzel funkce uvádí všechny funkce, které ji volat a využívání paměti rozhraním .NET a dat časování pro funkci.  
  
 Hodnoty v zobrazení stromu volání jsou pro funkce instancí, které byly volá funkci nadřazené ve stromové struktuře volání. Procentní hodnoty se počítá srovnáním hodnotu instance funkce pro celkový počet nebo velikost přidělení v profilaci spustit.  
  
## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu aktivní provádění  
 Zobrazení stromu volání můžete rozbalit a zvýraznit cestu spouštění procesu nebo funkce, která vytvořila na největší nebo většinu objektů paměti. Zobrazení Nejaktivnější cesty, klikněte pravým tlačítkem na proces nebo funkce a pak klikněte na tlačítko **rozbalte aktivní trase**.  
  
## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání  
 Každý proces v profilaci spuštění se zobrazí jako kořenový uzel. Počáteční uzel zobrazení stromu volání můžete nastavit tak, že kliknete pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a potom vyberete **nastavit kořenové**.  
  
 Pokud nastavíte kořenového uzlu, můžete eliminovat všechny položky ze zobrazení s výjimkou podstrom vybraného uzlu. Můžete resetovat kořenový uzel zpět do uzlu prohlížené; v okně zobrazení stromu volání klikněte pravým tlačítkem a vyberte **resetovat kořenové**.  
  
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
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Režijní náklady na čas výhradní testu**|Čas režie pro tuto funkci, která je způsobeno tím instrumentace. Režijní náklady na test odečtení od sebe výhradní.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci a jeho podřízené funkce způsobený instrumentace. Test režie odečtení od sebe (včetně).|  
|**Typ**|Kontext funkce:<br /><br /> -   **0** -aktuální funkce<br />-   **1** -funkci, která volá funkci current<br />-   **2** -funkci, která volá funkci current<br /><br /> Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Název kořenové – funkce**|Název aktuální funkce. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 (Včetně) hodnot paměti .NET funkce znamenat počet (přidělení) a velikost (bajty) objektů, které byly vytvořeny tak, že funkce a funkce, které byly volá funkci.  
  
 Hodnoty výhradní paměti označují, počtu a velikosti objektů, které byly vytvořeny kódu v těle funkce a ne funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Přidělení (včetně).**|Počet objektů, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Tato hodnota zahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly včetně přidělení instancí funkce, které byly volá funkci nadřazené ve stromové struktuře volání.|  
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Toto číslo nezahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly výhradní přidělení instancí funkce, které byly volá funkci nadřazené ve stromové struktuře volání.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas zahrnuje času stráveného v funkce, které byly volá funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|Celkový počet uplynulý čas včetně všechna volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**% Uplynulá doba (včetně).**|Procento celkového počtu uplynulý čas včetně času stráveného při celková doba uplynulá včetně této funkce při volání funkce nadřazené ve stromové struktuře volání spuštění profilování.|  
|**Průměr uplynulý čas včetně čas**|Průměr uplynulý čas včetně volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Maximální uplynulá doba (včetně).**|Maximální uplynulý čas včetně volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Min uplynulý čas včetně čas**|Minimální uplynulý čas včetně volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace. Čas však nezahrnuje času stráveného v funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|Celkový počet uplynulý čas výhradní všechna volání této funkce při volání funkce nadřazené ve stromu volání.|  
|**Uplynulý čas výhradní %**|Procento celkového počtu uplynul výhradní času stráveného při celková doba uplynulá výhradní této funkce při volání funkce nadřazené ve stromové struktuře volání spuštění profilování.|  
|**Průměr uplynulý exkluzivní čas**|Průměr uplynulý čas výhradní volání této funkce při volání funkce nadřazené ve stromu volání.|  
|**Maximální uplynulá doba výhradní**|Maximální uplynulý čas výhradní volání této funkce při volání funkce nadřazené ve stromu volání.|  
|**Min uplynulý exkluzivní čas**|Minimální uplynulý čas výhradní volání této funkce při volání funkce nadřazené ve stromu volání.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace. Čas nezahrnuje času stráveného v podřízené funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|Celkový počet aplikací čas včetně všechna volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Aplikace % času (včetně).**|Procento celkového počtu uplynulý čas (včetně) času stráveného v čase (včetně). Celkový počet aplikací této funkce při volání funkce nadřazené ve stromové struktuře volání spuštění profilování.|  
|**Prům. čas včetně aplikace**|Průměrná aplikace čas včetně volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Maximální doba včetně aplikace**|Čas (včetně). maximální aplikace volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Doba včetně aplikace min.**|Čas včetně minimální aplikace volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Aplikace hodnot, které označují času stráveného ve funkci, s výjimkou času stráveného v podřízené funkce, které byly volá funkci. Čas také vyloučí volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|Celkový počet aplikací čas výhradní všechna volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Aplikace % výhradní čas**|Procento celková doba uplynulá výhradní profilování spuštění, které byl stráven výhradní včas celkový aplikace této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Prům. čas výhradní aplikace**|Průměrná aplikace čas výhradní volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Maximální doba výhradní aplikace**|Čas výhradní maximální aplikace volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|  
|**Doba výhradní aplikace min.**|Čas výhradní minimální aplikace volání této funkce při volání funkce nadřazené ve stromové struktuře volání.|