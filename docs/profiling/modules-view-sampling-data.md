---
title: Zobrazení modulů – vzorkování dat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ead219ddf482af5917842118d386c6fefe67973
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74772711"
---
# <a name="modules-view---sampling-data"></a>Zobrazení modulů – vzorkování dat
Zobrazení modulů dat vzorkování zobrazuje údaje o výkonu, které jsou seskupeny podle modulů, které byly v datech profilace odebrány. Každý modul je kořenovým adresářem hierarchického stromu. Ukázkové funkce modulu jsou uvedeny pod uzlem modulu.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Pokud byla funkce prováděna při shromáždění vzorků (to znamená, že funkce byla v horní části zásobníku volání), zdrojové řádky a adresy instrukcí, které byly spuštěny, jsou uvedeny pod uzlem funkce. Vzhledem k tomu, že data jsou shromažďována pro zdrojový řádek nebo ukazatel instrukcí při provádění řádku nebo instrukce, jsou všechny a exkluzivní hodnoty vždy stejné pro data řádku i pro data instrukcí.

|Sloupec|Popis|
|------------|-----------------|
|**Name**|Název modulu, funkce, čísla řádku nebo adresy ukazatele na instrukci.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci, řádek nebo ukazatel na instrukci.|
|**Cesta k modulu**|Cesta modulu obsahujícího ukazatel modulu, funkce, řádku nebo instrukce.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Vzorky včetně**|– Pro funkci je proveden počet vzorků, ve kterých byla tato funkce nebo funkce volána touto funkcí. To znamená, že počet ukázek zásobníku volání, které tuto funkci obsahují.<br />– Pro modul je počet vzorků, ve kterých byla spuštěna alespoň jedna funkce z modulu.<br />– Pro řádek nebo instrukci počet vzorků, ve kterém se tento řádek nebo instrukce spouští.|
|**% Včetně vzorků**|– Pro funkci nebo modul je procento všech vzorků v průběhu profilace, které byly zahrnuté do vzorků této funkce nebo modulu.<br />– Pro řádek nebo instrukci je procentuální podíl všech vzorků v profilaci spuštěných, ve kterém se tento řádek nebo instrukce spouští.|
|**Exkluzivní vzorky**|– Pro funkci je počet vzorků zásobníku volání, ve kterých byla tato funkce přímo spuštěna; To znamená počet vzorků, ve kterých byla tato funkce v horní části zásobníku volání.<br />– Pro modul součet exkluzivních vzorků funkcí v modulu.<br />– Pro řádek nebo instrukci počet vzorků, ve kterém se tento řádek nebo instrukce spouští.|
|**% Exkluzivních vzorků**|– Pro funkci nebo modul je procento všech ukázek v profilovém spuštění, které byly exkluzivními ukázkami této funkce nebo modulu.<br />– Pro řádek nebo instrukci je procentuální podíl všech vzorků v profilaci spuštěných, ve kterém se tento řádek nebo instrukce spouští.|

## <a name="see-also"></a>Viz také
- [Zobrazení modulů – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
