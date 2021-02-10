---
title: Zobrazení sporů prostředků – data kolizí | Microsoft Docs
description: Přečtěte si, jak zobrazení kolizí prostředků vypisuje data kolizí pro prostředky, které byly zdrojem událostí sporu.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eac43dca403479d4a19ee9bbf9d5291f4db3aad0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952691"
---
# <a name="resource-contentions-view---contention-data"></a>Zobrazení kolizí prostředku – data kolizí
Zobrazení sporu prostředků uvádí data kolizí pro prostředky, které byly zdrojem událostí sporu. K události sporu dojde, když je funkce ve vlákně vynucena čekat na přístup k prostředku, protože funkce v jiném vlákně získala výhradní přístup k prostředku. Každý prostředek je kořenovým uzlem stromu volání, který zobrazuje cesty provádění funkce, jejichž výsledkem jsou události sporů.

## <a name="data-values"></a>Hodnoty dat

### <a name="resource-values"></a>Hodnoty prostředků
 Data v řádku prostředků zobrazují celkový čas, kdy byl přístup k prostředku zablokován v datech profilace a celkový počet událostí sporů, ke kterým došlo z důvodu konfliktu přístupu k tomuto prostředku. Zahrnuté a exkluzivní hodnoty pro prostředek jsou vždycky stejné.

### <a name="function-values"></a>Hodnoty funkcí
 Hodnoty funkcí jsou založené na instancích funkce, ke které došlo v cestě spuštění reprezentované ve stromu volání.

- Exkluzivní hodnoty jsou založeny na událostech, k nimž došlo v případě, že funkce prováděla příkazy v těle své funkce. Události, ke kterým došlo ve funkcích, které byly volány funkcí, nejsou zahrnuty ve výhradních hodnotách.

- Hodnoty včetně hodnot jsou založené na událostech, k nimž došlo při provádění funkce nebo funkce volané funkcí.

### <a name="percentage-values"></a>Procentuální hodnoty
 Procentuální hodnoty jsou založené na celkových událostech času nebo kolizí v datech profilace. Pokud je sestava nebo zobrazení běhu profilování filtrováno, použije se jako celková hodnota pouze zablokované časy a spory ve filtrovaných datech.

## <a name="navigating-the-resource-allocation-view"></a>Navigace v zobrazení přidělení prostředků

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název prostředku nebo funkce.|
|**Výhradní čas zablokování**|– Pro prostředek je celkový čas, kdy byl přístup k prostředku zablokován a způsobil, že vlákno čeká.<br />– Pro funkci, čas, kdy byly tyto instance funkce zablokovány přístupu k nadřazenému prostředku, pokud funkce prováděla kód v těle funkce. Čas zablokování ve funkcích, které byly volány funkcí, není zahrnutý.|
|**% Výhradního času zablokování**|– U prostředku je procento veškerého času zablokování v datech profilace, která byla zablokovaná čas tohoto prostředku.<br />– Pro funkci je procento veškerého času zablokování v datech profilace, která byla exkluzivně zablokovaná během těchto instancí funkcí.|
|**Exkluzivní spory**|– Pro prostředek je to celkový počet zablokovaných přístup k prostředku a způsobil, že vlákno čeká.<br />– Pro funkci, kolikrát byly tyto instance funkce zablokované přístupu k nadřazenému prostředku, pokud funkce prováděla kód v těle funkce. Blokování událostí ve funkcích, které byly volány funkcí, není zahrnuto.|
|**% Výhradních sporů**|– V případě prostředku je procento všech událostí sporů v datech profilace, které byly pro přístup k tomuto prostředku události sporu.<br />– Pro funkci je procento všech událostí sporů v datech profilace, které byly exkluzivní události kolizí těchto instancí funkcí pro nadřazený prostředek.|
|**Celková doba zablokování**|– Pro prostředek je celkový čas, kdy byl přístup k prostředku zablokován a způsobil, že vlákno čeká.<br />– Pro funkci, čas, kdy tyto instance funkce nebo jakékoli funkce volané instancemi byly zablokovány přístupu k nadřazenému prostředku, pokud funkce prováděla kód v těle funkce.|
|**% Celkového času zablokování**|– U prostředku je procento veškerého času zablokování v datech profilace, která byla zablokovaná čas tohoto prostředku.<br />– Pro funkci je procento veškerého času zablokování v běhu profilace, které se zablokovalo v čase těchto instancí funkce.|
|**Celkové spory**|– Pro prostředek je to celkový počet zablokovaných přístup k prostředku a způsobil, že vlákno čeká.<br />– Pro funkci je procento všech událostí kolizí v rámci profilace běhu, u kterých byly zahrnuté události kolizí těchto instancí funkcí pro nadřazený prostředek.|
|**% Celkových sporů**|– V případě prostředku je procento všech událostí sporů v průběhu profilace, které byly pro přístup k tomuto prostředku události kolizí.<br />– Pro funkci, kolikrát byly tyto instance funkce zablokované přístupu k nadřazenému prostředku, pokud funkce prováděla kód v těle funkce. Blokování událostí ve funkcích, které byly volány funkcí, není zahrnuto.|
|**Obsah**|Hloubka této funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) procesu, ve kterém byla funkce prováděna.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
