---
title: Zobrazení volající / volaný – Data vzorkování paměti .NET | Dokumentace Microsoftu
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
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edeccd8318de36a09a9191a30274ff342cb7a41d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816785"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Zobrazení volající/volaný – Data vzorkování paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení volající/volaný zobrazuje data pro vybrané funkce a její nadřazené a podřízené funkce profilování paměti .NET. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Aktuální funkce** se zobrazí v mřížce střední a zobrazuje informace o vybrané funkce profilace sledováním využívání paměti. Hodnoty zahrnují všechny vzorky volání funkce.  
  
 **Funkce, které volaly aktuální funkcí** se zobrazí v hlavní mřížky, a zobrazuje množství hodnota vybranou funkci (aktuální), který byl vygenerován ve volání funkce volajícího (nadřazené).  
  
 **Funkce, které byly volány aktuální funkcí** se zobrazí v mřížce dolů a zobrazuje paměti data profilování pro volaných (podřízený) funkcí z vybrané funkce při podřízené funkce byla volána aktuální funkce.  
  
 Klikněte dvakrát na volající nebo volaný funkce řádku provádět, který řádek aktuální funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce.|  
|**Typ**|Kontext funkce:<br /><br /> **0** -aktuální funkce<br /><br /> **1** – funkce, která volá aktuální funkci<br /><br /> **2** – funkce, která volá aktuální funkci<br /><br /> Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**úroveň**|Hloubka funkce ve stromu volání. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Celkově přidělení**|-Pro aktuální funkci Počet objektů, které byly přiděleny podle funkce při spuštění profilace. Toto číslo zahrnuje objekty, které byly vytvořeny ve volaných funkcí.<br />-Pro volající funkci, počet celkových přidělení aktuální funkce, které byly vytvořeny voláním z této funkce.<br />-Pro volaných funkce počet objektů, které byly přiděleny instancí této funkce, které byly volány aktuální funkcí. Číslo obsahuje přidělení, které byly provedeny pomocí funkcí, které byly volány volaných funkcí.|  
|**% Celkových přidělení**|Procento všech objektů, které byly vytvořeny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní přidělení**|-Pro funkci aktuální počet objektů, které se vytvořily při provádění funkce kódu těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkce.<br />-Pro volající funkci, počet výhradních přidělení aktuální funkce, které byly vytvořeny voláním z této funkce.<br />-Pro volaných funkce počet objektů, které byly vytvořeny podle instance této funkce, které byly volány aktuální funkcí. Číslo nezahrnuje objekty, které byly vytvořeny pomocí funkcí, které byly volány volaných funkcí.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly vytvořeny v profilování, která se celkově přidělení této funkce.|  
|**Celkově bajtů**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny podle funkce při spuštění profilace. Číslo obsahuje paměti, který se ve funkcích, které byly volány touto funkcí.<br />-Pro volající funkci Počet celkových bajtů, které byly generovány z aktuální funkce volání volající funkce.<br />-Pro volaných funkcí počet bajtů, které byly přiděleny instancí této funkce, které byly vytvořeny voláním z aktuální funkce. Číslo obsahuje počet bajtů, které byly přiděleny pomocí funkcí, které byly volány volaných funkcí.|  
|**% Celkových bajtů**|Procento bajtů paměti, které byly přiděleny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní bajty**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny podle funkce při spuštění profilace. Toto číslo nezahrnuje paměti, která byla přidělena pomocí funkcí, které byly volány aktuální funkcí.<br />-Pro volající funkci, počet výhradní bajty aktuální funkce, které byly vytvořeny voláním z volající funkce.<br />-Pro volaných funkcí počet bajtů, které byly přiděleny instancí funkce, které byly vytvořeny voláním z aktuální funkce. Počet bajtů, které byly přiděleny pomocí funkcí, které byly volány funkcí volaných neobsahuje.|  
|**% Výhradních bajtů**|Procento všech počet bajtů paměti, které byly přiděleny v profilování, které byly výhradních přidělení této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení volající/volaný – Data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Volající / volaný zobrazení – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)   
 [Zobrazení volající/volaný – Data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)



