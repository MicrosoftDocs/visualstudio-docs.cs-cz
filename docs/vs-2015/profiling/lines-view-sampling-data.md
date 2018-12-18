---
title: Zobrazení řádků – vzorkování dat | Dokumentace Microsoftu
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
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cd360e120b9747a16234aa28c42912de4254b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734666"
---
# <a name="lines-view---sampling-data"></a>Zobrazení řádků – vzorkování dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Řádky zobrazení dat vzorkování obsahuje údaje o výkonu pro příkazy, které byla spuštěna při ukázky byly shromážděny v profilaci spouštět.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Ve zdrojovém souboru příkaz se týkají více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden výraz. Příkaz je identifikován následující:  
  
- Zdrojový soubor, který obsahuje Function – příkaz  
  
- Funkce, která obsahuje příkaz.  
  
- Zdrojový řádek, ve kterém začíná příkaz.  
  
- Znak ve zdrojovém řádku, ve kterém se spustí příkaz.  
  
- Řádku zdroje, u které končí příkaz.  
  
- Znak ve zdrojovém řádku, kdy příkaz skončí.  
  
  Sloupec název řádek obsahuje seřaditelné zřetězení těchto dat identifikátor.  
  
  Podle definice příkazu nevolá dalších funkcí. Proto jsou uvedeny pouze výhradní hodnoty.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje řádek funkce.|  
|**Cesta modulu**|Cesta k napadenému modulu, která obsahuje řádek funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje řádek – funkce|  
|**Název funkce**|Název funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Počáteční adresa funkce.|  
|**Začátek řádku zdroje**|Počáteční řádek číslo ve zdrojovém souboru, ve kterém byl shromážděn této ukázce.|  
|**Konec řádku zdroje**|Koncové číslo řádku ve zdrojovém souboru, ve kterém byl shromážděn této ukázce.|  
|**Počáteční znak zdrojového kódu**|Odsazení počátečního znaku ve zdrojovém souboru řádku shromáždění této ukázce.|  
|**Koncový znak zdrojového kódu**|Posun poslední znak v řádku zdrojového souboru shromáždění této ukázce.|  
|**Název čáry**|Identifikátor generovaný profileru řádku pomocí následující syntaxe:`Source File`**; [** `Line Number Start` **,**`Character Start`**] ->; [**`Line Number End`**,**`Character End`**]**|  
|**Výhradní vzorky**|Celkový počet vzorků, které byly shromážděny při provádění funkce řádku.|  
|**% Výhradních vzorků**|Procento všechny ukázky v běhu profilování, které byly shromážděny při provádění funkce řádku.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení řádků – Vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)



