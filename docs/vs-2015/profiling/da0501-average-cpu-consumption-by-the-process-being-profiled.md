---
title: 'DA0501: Průměr Spotřeby procesoru profilovaným Procesem. | Dokumentace Microsoftu'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155777"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Průměr Spotřeby procesoru profilovaným Procesem.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA501 |  
| Kategorie | Monitorování prostředků |  
| Metoda profilování | Vše |  
| Zpráva | Průměrná spotřeba procesoru procesem profilace. |  
| Typ pravidla | Informace |  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva oznamuje procento času, po který procesor byl zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je průměr ve všech intervalech měření, v nichž byl proces profilace aktivní. Hodnota Value může být větší než 100% na počítači s více než jedním procesorem.  
  
## <a name="how-to-use-rule-data"></a>Jak používat data pravidla  
 Použijte hodnotu pravidla pro porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v různých testovacích scénářích.
