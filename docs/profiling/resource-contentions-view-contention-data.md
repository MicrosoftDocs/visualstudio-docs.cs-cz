---
title: Zobrazení kolizí prostředku – Data kolizí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e33a27d5f2b14effc9d8a90e903b34822d81edfb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/19/2018
ms.locfileid: "31584136"
---
# <a name="resource-contentions-view---contention-data"></a>Zobrazení kolizí prostředku – Data kolizí
Zobrazení kolizí prostředku uvádí data kolizí pro prostředky, které byly zdroj kolizní události. Kolizní události nastane, když je funkce ve vlákně vynutit čekání na přístup k prostředku, protože funkce v jiné vlákno má získat výhradní přístup k prostředku. Každý prostředek je kořenový uzel stromu volání, která zobrazuje funkce cesty provádění, jejichž výsledkem kolizní události.  
  
## <a name="data-values"></a>Hodnoty data  
  
### <a name="resource-values"></a>Hodnoty prostředků  
 Data v řádku prostředků zobrazí celkový čas, který byl zablokován přístup k prostředku v data profilování a celkový počet kolizní události, které došlo k chybě z důvodu konfliktu přístup k tomuto prostředku. (Včetně) a výhradní hodnoty prostředku jsou vždy stejné.  
  
### <a name="function-values"></a>Hodnoty funkce  
 Funkce hodnoty jsou založené na instance funkce, která došlo k chybě v cestě k provádění reprezentované ve stromové struktuře volání.  
  
-   Hodnot, které jsou založené na události, které došlo k chybě při provádění funkce příkazy v jeho tělo funkce. Hodnot, které nejsou součástí událostí, které nastaly v funkce, které byly volá funkci.  
  
-   (Včetně). hodnoty jsou založené na události, které došlo k chybě při provádění funkce nebo funkce volá funkci.  
  
### <a name="percentage-values"></a>Procentní hodnoty  
 Procentní hodnoty jsou založené na celkový čas nebo kolizní událostí v data profilování. Pokud je filtrován sestavu nebo zobrazení profilace spustit, jenom blokovaných čas a kolizí v filtrovaných dat se používají jako celkovou hodnotu.  
  
## <a name="navigating-the-resource-allocation-view"></a>Navigace zobrazení přidělení prostředků  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název prostředku nebo funkce.|  
|**Výhradní blokované čas**|-Pro prostředek celkový čas tento přístup k prostředku byl blokovaný a způsobila vlákno čekání.<br />-Pro funkce, čas, který tyto instance funkce měla přístup nadřazený prostředek při funkce provádění kódu v těle funkce zablokován. Blokované čas v funkce, které byly volá funkci není součástí.|  
|**Výhradní blokované čas: %**|-Pro prostředek, procento všech blokovaných času v profilaci data, která byla blokována času tento prostředek<br />-Pro funkci, procento všech blokovaných času v profilaci data, která byla výhradní blokované čas instancí tyto funkce.|  
|**Výhradní kolizí**|-Pro prostředek byl celkový počet pokusů, které přístup k danému prostředku blokovaný a způsobila vlákno čekání.<br />-Pro funkce, počet pokusů, které tyto instance funkce měla přístup nadřazený prostředek při funkce provádění kódu v těle funkce zablokován. Blokování události v funkce, které byly volá funkci nejsou zahrnuty.|  
|**% Výhradní kolizí**|-Pro prostředek, procento všech kolizní události v profilaci data, která měla kolizní události pro přístup k tomuto prostředku.<br />-Pro funkce, procento všech kolizní události v profilaci data, která měla výhradní kolizní události instancí tyto funkce pro nadřazený prostředek.|  
|**Blokované čas (včetně).**|-Pro prostředek celkový čas tento přístup k prostředku byl blokovaný a způsobila vlákno čekání.<br />-Pro funkci byly ve chvíli, tyto instance funkce nebo všechny funkce volá instance blokovaný přístup k nadřazený prostředek při funkce provádění kódu v těle funkce.|  
|**Včetně blokované čas: %**|-Pro prostředek, procento všech blokovaných času v profilaci data, která byla blokována času tento prostředek<br />-Pro funkci procento všech blokovaných času v profilaci spuštění, který byl včetně blokované čas instancí tyto funkce.|  
|**Kolizí (včetně).**|-Pro prostředek byl celkový počet pokusů, které přístup k danému prostředku blokovaný a způsobila vlákno čekání.<br />-Pro funkci procento všech kolizní události v profilaci spuštění, které byly včetně kolizní události instancí tyto funkce pro nadřazený prostředek.|  
|**% Kolizí (včetně).**|-Pro prostředek procento všech kolizní události v profilaci spuštění, které byly kolizní události pro přístup k tomuto prostředku.<br />-Pro funkce, počet pokusů, které tyto instance funkce měla přístup nadřazený prostředek při funkce provádění kódu v těle funkce zablokován. Blokování události v funkce, které byly volá funkci nejsou zahrnuty.|  
|**úroveň**|Hloubka této funkce ve stromové struktuře volání. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) procesu, ve kterém se provádí funkce.|  
|**Název procesu**|Název procesu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|