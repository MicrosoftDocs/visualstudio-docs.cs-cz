---
title: 'DA0501: Průměr Spotřeby procesoru profilovaným Procesem. | Dokumenty Microsoft'
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
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 076afd65d356f319357221c0d33489895311dcc3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759541"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Průměr Spotřeby procesoru profilovaným Procesem.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA501 |  
| Kategorie | Sledování prostředků |  
| Metoda profilace | Všechny |  
| Zpráva | Průměr spotřeby procesoru profilovaným procesem. |  
| Typ pravidla | Informace |  
  
 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva znamená procentuální hodnotu času, který byl procesor zaneprázdněný, provádění instrukcí z aplikace. Hlášená hodnota je průměrem přes všechny intervaly měření, ve kterých byl aktivní profilovaný proces. Hodnota může být větší než 100 % na počítači s více než jeden procesor.  
  
## <a name="how-to-use-rule-data"></a>Jak používat Data pravidla  
 Hodnota pravidla použijte k porovnání výkonu různých verzí nebo sestavení tohoto programu nebo porozumět výkonu aplikace v rámci různých testovacích scénářů.



