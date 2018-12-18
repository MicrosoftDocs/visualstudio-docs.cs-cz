---
title: 'DA0004: Vysoké využití procesoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87f418c8f145d13dee575c9d45d192a59547e6a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920882"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Vysoké využití procesoru

|||  
|-|-|  
|Id pravidla|DA0004|  
|Kategorie|Použití nástroje pro profilaci|  
|Metod profilace|Instrumentace<br /><br /> Vzorkování|  
|Zpráva|Využití procesoru je trvale vyšší než 75 %. Zvažte použití režimu vzorkování pro aplikace vázané na procesor.|  
|Typ pravidla|Informace o|  

 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  

## <a name="cause"></a>příčina  
 Využití procesoru (CPU) je vysoká v profilaci dat, která byla shromážděna pomocí metody instrumentace. Zvažte použití při profilování Procesorem vázán aplikace metoda profilování vzorkování.  

## <a name="rule-description"></a>Popis pravidla  
 Během tohoto spuštění profilování byl trvale zaneprázdněn procesoru (nebo procesory). Vysoké využití procesoru můžete určit aplikace vázané na procesor. Instrumentovaná profily nejsou nejúčinnější způsob pro scénáře využití procesoru. Vzorkování je efektivnější, pokud provádíte profilaci aplikace, které tráví většinu svého času provádění instrukcí na procesor.  

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Zvažte profilaci vaší aplikace znovu pomocí metody odběru vzorků namísto metody instrumentace, pokud vyžadujete funkce časování nebo více zájem o porozumění vstupu a výstupu než problémových míst procesoru.