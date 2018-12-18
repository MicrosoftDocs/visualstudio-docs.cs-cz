---
title: Zobrazení kolizí prostředku – Data kolizí | Dokumentace Microsoftu
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
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dddc9c85731137c6499e976b4b571396af297f7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810348"
---
# <a name="resource-contentions-view---contention-data"></a>Zobrazení kolizí prostředku – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení kolizí prostředku obsahuje data kolize prostředků, které byly zdroj kolizní události. Kolize událost nastane, pokud funkce ve vlákně je nuceni čekat přístup k prostředku, protože funkce v jiném vlákně má získat výhradní přístup k prostředku. Každý prostředek je kořenový uzel stromu volání, která zobrazuje cesty spuštění funkce, jejichž výsledkem kolizní události.  
  
## <a name="data-values"></a>Hodnoty dat  
  
### <a name="resource-values"></a>Hodnoty prostředků  
 V řádku zdroje dat zobrazuje celkový čas, který byl zablokován přístup k prostředku v Profilování dat a celkový počet kolizní události, ke kterým došlo kvůli konfliktu přístup k tomuto prostředku. Zahrnuté a výhradní hodnoty prostředku jsou vždy stejné.  
  
### <a name="function-values"></a>Hodnoty – funkce  
 Hodnoty funkcí jsou založeny na instance, ke které došlo v provádění cestu ve stromu volání funkce.  
  
-   Výhradní hodnoty jsou založené na události, ke kterým došlo při provádění funkce příkazy v těle jeho funkce. Události, ke kterým došlo ve funkcích, které byly volány funkce nejsou součástí výhradní hodnoty.  
  
-   Celkové hodnoty jsou založené na události, ke kterým došlo při provádění funkce nebo funkce volané funkce.  
  
### <a name="percentage-values"></a>Procento hodnoty  
 Procento hodnoty jsou založeny na celkový čas nebo kolize události v dat profilování. Pokud je filtrování sestav nebo zobrazení běhu profilování, čas zablokování a tento počet sporů: v filtrovaná data se používají jako celková hodnota.  
  
## <a name="navigating-the-resource-allocation-view"></a>Navigace zobrazení přidělení prostředků  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název prostředku nebo funkce.|  
|**Výhradní čas zablokování**|-Pro určitý prostředek celkový čas, které přístup k prostředku se zablokuje a způsobila vlákno čekání.<br />-Pro funkci, čas, který tyto instance funkce se zablokoval přístup k nadřazeným prostředkem při provádění kódu funkce v těle funkce. Čas zablokování ve funkcích, které byly volány funkce není součástí.|  
|**% Výhradního času zablokování**|-Pro určitý prostředek, procento času zablokování všech dat profilování, která se zablokovala, čas tento prostředek<br />-Pro určitou funkci, procento času zablokování všech dat profilování, která byla výhradní čas zablokování těchto instancí funkce.|  
|**Výhradní spory**|– Celkový počet případů, kdy se přístup k prostředku byl pro prostředek, zablokuje a způsobila vlákno čekání.<br />-Pro funkci, počet případů, kdy se tyto instance funkce se zablokoval přístup k nadřazeným prostředkem při provádění kódu funkce v těle funkce. Blokujících událostí ve funkcích, které byly volány funkce nejsou zahrnuty.|  
|**% Výhradních sporů**|-Pro prostředek, procento všech kolizní události v profilaci dat, které byly kolizní události pro přístup k tomuto prostředku.<br />-Pro funkci, procento všech kolizní události v profilaci dat, které byly exkluzivní kolizní události z těchto instancí funkce pro nadřazený prostředek.|  
|**Celkový čas zablokování**|-Pro určitý prostředek celkový čas, které přístup k prostředku se zablokuje a způsobila vlákno čekání.<br />-Pro určitou funkci byly čas, který tato instance funkce nebo jakékoli funkce volány instance blokovat přístup k nadřazeným prostředkem při provádění kódu funkce v těle funkce.|  
|**% Celkového času zablokování**|-Pro určitý prostředek, procento času zablokování všech dat profilování, která se zablokovala, čas tento prostředek<br />-Pro určitou funkci procento všech času zablokování při spuštění, který profilace byla celkový čas zablokování těchto instancí funkce.|  
|**Celkově sporů**|– Celkový počet případů, kdy se přístup k prostředku byl pro prostředek, zablokuje a způsobila vlákno čekání.<br />-Pro určitou funkci procento všech kolizní události v profilování, které byly včetně kolizní události z těchto instancí funkce pro nadřazený prostředek.|  
|**% Celkových sporů**|-Pro určitý prostředek procento všech kolizní události v profilování, která se kolizní události pro přístup k tomuto prostředku.<br />-Pro funkci, počet případů, kdy se tyto instance funkce se zablokoval přístup k nadřazeným prostředkem při provádění kódu funkce v těle funkce. Blokujících událostí ve funkcích, které byly volány funkce nejsou zahrnuty.|  
|**úroveň**|Hloubka tuto funkci ve stromu volání. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) proces, ve kterém funkce byla spuštěna.|  
|**Název procesu**|Název procesu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|



