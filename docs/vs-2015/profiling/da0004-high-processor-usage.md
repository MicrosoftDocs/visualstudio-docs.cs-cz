---
title: 'DA0004: vysoké využití procesoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0e14a7400b937c56c2aac49a43d1d59cf96eba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158701"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Vysoké využití procesoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0004 |  
| Kategorie | Využití Nástroje pro profilaci |  
| Metody profilování | Vzorkování instrumentace |  
| Zpráva | Využití procesoru je konzistentně vyšší než 75%. Zvažte použití režimu vzorkování pro aplikace vázané na procesor. |  
| Typ pravidla | Informace |  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.  
  
## <a name="cause"></a>Příčina  
 Využití procesoru (CPU) bylo výrazně vysoké v datech profilace, která byla shromážděna pomocí metody instrumentace. Při profilování aplikace vázané na procesor zvažte použití metody profilace vzorkování.  
  
## <a name="rule-description"></a>Popis pravidla  
 Během tohoto spuštění profilace byly procesory (nebo procesory) konzistentně velmi zaneprázdněné. Vysoké využití procesoru může označovat aplikaci vázanou na procesor. Instrumentované profily nejsou většinou nejúčinnější způsob, jak prozkoumat scénáře využití procesoru. Vzorkování je obvykle efektivnější, pokud pracujete s aplikacemi, které tráví spoustu času při provádění instrukcí v procesoru.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Zvažte možnost profilování aplikace znovu pomocí metody vzorkování namísto metody instrumentace, pokud nepožadujete časování funkcí nebo máte větší zájem o porozumění vstupu/výstupu, než je problémová místa pro procesor.
