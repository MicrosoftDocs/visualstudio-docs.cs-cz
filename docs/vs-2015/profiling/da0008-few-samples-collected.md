---
title: 'DA0008: shromážděno málo ukázek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03fd9b6fd794320faf76119616900b79d5bf4333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187860"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Shromážděno málo vzorků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0008 |  
| Kategorie | Využití Nástroje pro profilaci |  
| Metoda profilování | Vzorkování |  
| Zpráva | Bylo shromážděno pouze několik ukázek. Zvažte delší spuštění nebo rychlejší vzorkovací frekvenci pro více významných výsledků. |  
| Typ pravidla | Informace |  
  
## <a name="cause"></a>Příčina  
 Při spuštění profilace bylo shromážděno pouze několik ukázek.  
  
## <a name="rule-description"></a>Popis pravidla  
 Při použití metody vzorkování byste měli shromáždit statisticky významný počet vzorků, abyste se ujistili, že data představují skutečné chování programu. Chcete-li minimalizovat chyby vzorkování, měli byste se pokusit shromáždit alespoň 1000 vzorků chování při spuštění instrukcí programu. Pokud neshromáždíte dostatek ukázek, můžete při analýze dat profilace být zauváděna do kódu.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Vezměte v úvahu profilaci delšího spuštění aplikace nebo pomocí rychlejšího vzorkovacího kurzu Získejte statisticky významné výsledky. Informace o tom, jak změnit vzorkovací frekvenci v integrovaném vývojovém prostředí sady Visual Studio, naleznete v tématu [How to: zvolit události vzorkování](../profiling/how-to-choose-sampling-events.md). Další informace o tom, jak změnit vzorkovací frekvenci při použití příkazového řádku Nástroje pro profilaci, najdete v tématu [Timer](../profiling/timer.md) v odkazu [VSPerfCmd](../profiling/vsperfcmd.md) .
