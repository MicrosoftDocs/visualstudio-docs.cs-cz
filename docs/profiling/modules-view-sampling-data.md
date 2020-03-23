---
title: Zobrazení modulů – vzorkovací data | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772711"
---
# <a name="modules-view---sampling-data"></a>Zobrazení modulů - vzorkovací data
Zobrazení modulů vzorkovacích dat zobrazuje údaje o výkonu seskupené podle modulů, které byly vzorkovány v datech profilování. Každý modul je kořenem hierarchického stromu. Vzorkované funkce modulu jsou uvedeny pod uzlničem modulu.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Pokud byla funkce spuštěna při shromažďování vzorků (to znamená, že funkce byla v horní části zásobníku volání), jsou pod uzlem funkce uvedeny zdrojové řádky a adresy instrukcí, které byly spuštěny. Vzhledem k tomu, že data jsou shromažďována pro zdrojový řádek nebo ukazatel instrukce při provádění řádku nebo instrukce, včetně a výhradní hodnoty jsou vždy stejné pro data řádku a data instrukce.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název modulu, funkce, čísla řádku nebo adresy ukazatele instrukce.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje ukazatel funkce, řádku nebo instrukce.|
|**Cesta modulu**|Cesta modulu, který obsahuje modul, funkce, řádek nebo ukazatel instrukce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Včetně vzorků**|- Pro funkci počet vzorků, ve kterých byla tato funkce nebo funkce, která byla volána touto funkcí, byla spuštěna; to znamená počet ukázek zásobníku volání, které obsahovaly tuto funkci.<br />- U modulu se počet vzorků, ve kterých byla spuštěna alespoň jedna funkce z modulu.<br />- Pro řádek nebo instrukce počet vzorků, ve kterých byl tento řádek nebo instrukce prováděny.|
|**Včetně vzorků %**|- Pro funkci nebo modul, procento všech vzorků v profilování spustit, které byly včetně vzorků této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech vzorků v profilování spustit, ve kterém byl tento řádek nebo instrukce provádění.|
|**Exkluzivní ukázky**|- Pro funkci počet ukázek zásobníku volání, ve kterém byla tato funkce přímo spuštěna; to znamená počet vzorků, ve kterých byla tato funkce v horní části zásobníku volání.<br />- Pro modul, součet exkluzivních vzorků funkcí v modulu.<br />- Pro řádek nebo instrukce počet vzorků, ve kterých byl tento řádek nebo instrukce prováděny.|
|**Exkluzivní vzorky %**|- Pro funkci nebo modul, procento všech vzorků v profilování spustit, které byly výhradní vzorky této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech vzorků v profilování spustit, ve kterém byl tento řádek nebo instrukce provádění.|

## <a name="see-also"></a>Viz také
- [Zobrazení modulů - odběr vzorků](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Pohled modulů - instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
