---
title: 'DA0003: mnoho ukázek jádra | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158714"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Velký počet vzorků jádra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0003 |  
| Kategorie | Využití Nástroje pro profilaci |  
| Metody profilování | Vzorkování |  
| Zpráva | V režimu jádra máte vysokou část ukázek. To může znamenat velký objem vstupně-výstupních aktivit nebo vysoké míry přepínání kontextu. Zvažte profilaci aplikace znovu pomocí režimu instrumentace. |  
| Typ pravidla | Informace |  
  
## <a name="cause"></a>Příčina  
 Významný podíl ukázek zásobníku volání, které byly shromážděny pro aplikaci, byly spuštěny v režimu jádra. Zvažte profilaci aplikace pomocí jiné metody profilace.  
  
## <a name="rule-description"></a>Popis pravidla  
 V systému Windows lze kód spustit buď v režimu jádra, nebo v uživatelském režimu. (Režim jádra se označuje taky jako privilegovaný režim.) V režimu jádra je spuštěn pouze systémový kód nízké úrovně, například ovladače zařízení. Aplikace v uživatelském režimu se může převést do režimu jádra, aby prováděla vstupně-výstupní operace, aby se čekalo na prvky synchronizace vlákna nebo procesu, nebo do systémových volání.  
  
 Vzorkování je nejúčinnější při profilování aplikací, které tráví většinu času při práci v uživatelském režimu. Počet vzorků, které byly shromážděny při spuštění aplikace v režimu jádra, může označovat časté vstupně-výstupní operace nebo může indikovat, že dojde k přepnutí kontextu. Ani jednu z těchto operací nelze prozkoumat pomocí metody vzorkování. Pokud jsou odebírány příliš mnoho vzorků režimu jádra, data vzorkování nemusí obsahovat dostatek vzorků uživatelského režimu, aby byly statisticky důležité.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Zvažte možnost profilování aplikace znovu pomocí jedné z následujících možností:  
  
- Profilujte pomocí metody instrumentace.  
  
- Zvyšte vzorkovací frekvenci a pokuste se shromáždit další ukázky v uživatelském režimu.
