---
title: Zobrazení volající volaný – Data vzorkování paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e2115f2f5c23d244d3a8650b46fff1f0f74689ec
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548114"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Zobrazení volající/volaný – data vzorkování paměti .NET
Zobrazení volající/volaný zobrazí data pro vybrané funkce a její nadřazené a podřízené funkce profilace sledováním využívání paměti .NET. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Funkci Current** se zobrazí v mřížce střední a zobrazuje informace o vybrané funkce profilace sledováním využívání paměti. Hodnoty zahrnují u všech vybraných volání funkce.  
  
 **Funkce, které volá funkci current** se zobrazí v horní mřížky, a zobrazuje množství hodnotu vybrané (aktuální) funkce, který byl vygenerován volání z funkce volající (nadřazené).  
  
 **Funkce, které byly volá funkci current** se zobrazí v mřížce dole, a zobrazuje paměti při volání funkce podřízené aktuální funkcí profilace data pro funkce volaný (podřízená) vybrané funkce.  
  
 Dvakrát klikněte na volající nebo volaný funkce řádek, aby který řádek aktuální funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce.|  
|**Typ**|Kontext funkce:<br /><br /> **0** -aktuální funkce<br /><br /> **1** -funkci, která volá funkci current<br /><br /> **2** -funkci, která volá funkci current<br /><br /> Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**úroveň**|Hloubka funkce ve stromové struktuře volání. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Přidělení (včetně).**|-Pro aktuální funkci Počet objektů, které byly přiděleny funkcí v profilaci spustit. Toto číslo zahrnuje objekty, které byly vytvořeny v volaný funkce.<br />-Pro volající funkce počet včetně přidělení aktuální funkce, které byly vygenerovány volání z této funkce.<br />-Pro funkci volaný, počet objektů, které byly přiděleny instancí této funkce, které byly volá funkci aktuální. Počet zahrnuje přidělení, které byly provedeny podle funkce, které byly volá funkci volaný.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní přidělení**|-Pro funkci aktuální počet objektů, které byly vytvořeny při funkce provádění kódu tělo funkce (to znamená, když funkce se v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volá funkci.<br />-Pro volající funkce počet výhradní přidělení aktuální funkce, které byly vygenerovány volání z této funkce.<br />-Pro funkci volaný, počet objektů, které byly vytvořeny instancí této funkce, které byly volá funkci current. Počet objektů, které byly vytvořené pomocí funkce, které byly volá funkci volaný neobsahuje.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Bajtů (včetně).**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny funkcí v profilaci spustit. Počet zahrnuje pamětí přidělenou ve funkcích, které byly volat pomocí této funkce.<br />-Pro volající funkci Počet včetně bajtů aktuální funkce, které byly vygenerovány z volání funkce volajícího.<br />-Pro funkci volaný, počet bajtů, které byly přiděleny instancí této funkce, které byly vygenerovány volání z aktuální funkce. Obsahuje počet bajtů, které byly přiděleny podle funkce, které byly volá funkci volaný.|  
|**% Bajtů (včetně).**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní bajtů**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny funkcí v profilaci spustit. Toto číslo nezahrnuje paměti, která byla přidělena funkce, které byly volá funkci aktuální.<br />-Pro volající funkce počet bajtů výhradní aktuální funkce, které byly vygenerovány volání z volající funkce.<br />-Pro funkci volaný, počet bajtů, které byly přiděleny instancemi funkce, které byly vygenerovány volání z aktuální funkce. Počet bajtů, které byly přiděleny podle funkce, které byly volá funkci volaný neobsahuje.|  
|**% Výhradní bajtů**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly výhradní přidělení této funkce.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení volající/volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Zobrazení volající/volaný – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)   
 [Zobrazení volající/volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)