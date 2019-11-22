---
title: 'DA0505: průměrné soukromé bajty přidělené pro proces, který je profilované | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab96f8f6dea40adcf18847cf9503fd934f7ed3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300463"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Průměr Nesdílených bajtů přidělených pro profilovaný Proces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0505 |  
| Kategorie | Správa prostředků |  
| Metoda profilování | Vše |  
| Zpráva | Tyto informace se shromáždily jenom pro informace. Čítač procesu soukromých bajtů měří virtuální paměť přidělenou procesem, který vytváříte profilování. Hodnota hlášené je průměr vypočítaný ve všech intervalech měření. |  
| Typ pravidla | Informace |  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva oznamuje průměrnou velikost virtuální paměti, kterou proces aktuálně přidělil v bajtech (nesdílené bajty). Soukromé bajty představují umístění virtuální paměti, která byla přidělena procesu, ke kterému lze přistupovat pouze v vláknech spuštěných uvnitř procesu.  
  
 Pro 32 procesy běžící na 32 počítači je horní limit soukromé části adresního prostoru procesu 2 GB. Pomocí přepínače [/3Gb](https://go.microsoft.com/fwlink/?LinkId=177831) Boot. ini můžou 32 procesy získat až 3 GB virtuální paměti. 32 proces, který běží na 64 počítači, může získat až 4 GB privátní virtuální paměti.  
  
 64 proces, který běží na 64 počítači, může získat až 8 TB privátní virtuální paměti.  
  
 Hodnota hlášené je průměrem ve všech intervalech měření, ve kterých je proces profilace aktivní.  
  
 Další informace o adresních prostorech procesu najdete v tématu [virtuální adresní prostor](https://go.microsoft.com/fwlink/?LinkId=177832) v dokumentaci ke službě Správa paměti systému Windows.  
  
## <a name="how-to-use-rule-data"></a>Jak používat data pravidla  
 Pomocí hlášené hodnoty můžete porovnávat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v rámci různých scénářů profilace.
