---
title: 'DA0502: maximální využití procesoru procesem profilování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a47a9c5964ccf15d2c609233eb600f39bc3ad2d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205925"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maximální spotřeba procesoru profilovaným procesem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0502 |  
| Kategorie | Monitorování prostředků |  
| Metoda profilování | Vše |  
| Zpráva | Toto pravidlo je pouze pro informace. Čítač procesu () \\ % času procesoru měří spotřebu procesoru procesu, který vytváříte profilování. Hodnota hlášené je maximální pozorována ve všech intervalech měření. |  
| Typ pravidla | Informační |  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva oznamuje maximální procento času, po který procesor zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je maximální hodnota hlášená mezi všemi měřicími intervaly, ve kterých je proces profilace aktivní. Procentuální hodnota může být větší než 100% na počítači s více než jedním procesorem.  
  
## <a name="how-to-use-the-rule-data"></a>Jak používat data pravidla  
 Použijte hodnotu pravidla pro porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v rámci různých scénářů profilace.
