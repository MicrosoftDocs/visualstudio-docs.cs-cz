---
title: Zobrazení konfliktů prostředků – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1607e594b6456d4da4396069d589160230b39680
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778333"
---
# <a name="resource-contentions-view---contention-data"></a>Zobrazení kolizí prostředku – data kolizí
Zobrazení Konflikty prostředků uvádí data kolizí pro prostředky, které byly zdrojem událostí kolizí. K události konfliktu dochází, když je funkce ve vlákně vynucena čekání na přístup k prostředku, protože funkce v jiném vlákně získala výhradní přístup k prostředku. Každý prostředek je kořenový uzel stromu volání, který zobrazuje cesty spuštění funkce, které vedly k událostem kolizí.

## <a name="data-values"></a>Datové hodnoty

### <a name="resource-values"></a>Hodnoty zdrojů
 Data v řádku prostředku zobrazuje celkový čas, po který byl v datech profilování zablokován přístup k prostředku, a celkový počet konfliktních událostí, ke kterým došlo z důvodu konfliktu přístupu k tomuto prostředku. Včetně a výhradní hodnoty pro prostředek jsou vždy stejné.

### <a name="function-values"></a>Hodnoty funkcí
 Hodnoty funkce jsou založeny na instancích funkce, ke kterým došlo v cestě spuštění reprezentované ve stromu volání.

- Výhradní hodnoty jsou založeny na událostech, ke kterým došlo, když funkce prováděla příkazy v těle své funkce. Události, ke kterým došlo ve funkcích, které byly volány funkcí, nejsou zahrnuty do výhradních hodnot.

- Včetně hodnoty jsou založeny na události, ke kterým došlo, když byla spuštěna funkce nebo funkce volané funkcí.

### <a name="percentage-values"></a>Procentní hodnoty
 Procentuální hodnoty jsou založeny na celkovém čase nebo konfliktních událostech v datech profilování. Pokud je sestava nebo zobrazení spuštění profilování filtrováno, použije se jako celková hodnota pouze blokovaný čas a konflikty ve filtrovaných datech.

## <a name="navigating-the-resource-allocation-view"></a>Navigace v zobrazení přidělení zdrojů

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název prostředku nebo funkce.|
|**Exkluzivní blokovaný čas**|- Pro prostředek celkový čas, který byl zablokován přístup k prostředku a způsobil vlákno čekat.<br />- Pro funkci čas, který tyto instance funkce byly zablokovány přístup k nadřazený prostředek, když funkce byla provádění kódu v těle funkce. Blokovaný čas ve funkcích, které byly volány funkcí, není zahrnut.|
|**Výhradní blokovaný čas %**|- Pro zdroj procento všech blokovaných čas v profilování dat, která byla blokována čas tohoto prostředku<br />- Pro funkci procento všech blokovaných čas v profilování dat, která byla výhradní blokovaný čas těchto instancí funkce.|
|**Exkluzivní tvrzení**|- U prostředku byl celkový počet, kolikrát byl přístup k prostředku zablokován a způsobil čekání vlákna.<br />- Pro funkci, kolikrát tyto instance funkce byly zablokovány přístup k nadřazený prostředek, když funkce byla provádění kódu v těle funkce. Blokování události ve funkcích, které byly volány funkce nejsou zahrnuty.|
|**Výhradní tvrzení %**|- Pro prostředek procento všech konfliktních událostí v datech profilování, které byly konfliktní události pro přístup k tomuto prostředku.<br />- Pro funkci procento všech konfliktních událostí v datech profilování, které byly výhradními konfliktními událostmi těchto instancí funkce pro nadřazený prostředek.|
|**Včetně blokovaného času**|- Pro prostředek celkový čas, který byl zablokován přístup k prostředku a způsobil vlákno čekat.<br />- Pro funkci čas, který tyto instance funkce nebo všechny funkce volané instance byly zablokovány přístup k nadřazený prostředek, když funkce byla provádění kódu v těle funkce.|
|**Včetně blokovaného času %**|- Pro zdroj procento všech blokovaných čas v profilování dat, která byla blokována čas tohoto prostředku<br />- Pro funkci procento všech blokovaných čas v profilování spustit, který byl včetně blokované čas těchto instancí funkce.|
|**Inkluzivní tvrzení**|- U prostředku byl celkový počet, kolikrát byl přístup k prostředku zablokován a způsobil čekání vlákna.<br />- Pro funkci procento všech konfliktních událostí v profilování spustit, které byly včetně konfliktní události těchto instancí funkce pro nadřazený prostředek.|
|**Inkluzivní tvrzení %**|- Pro prostředek procento všech konfliktních událostí v profilování spustit, které byly konfliktní události pro přístup k tomuto prostředku.<br />- Pro funkci, kolikrát tyto instance funkce byly zablokovány přístup k nadřazený prostředek, když funkce byla provádění kódu v těle funkce. Blokování události ve funkcích, které byly volány funkce nejsou zahrnuty.|
|**Úroveň**|Hloubka této funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu, ve kterém byla funkce spuštěna, id procesu.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
