---
title: Pravidla výkonu paměti a stránkování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf868164a8768b01793e6c5ec69b90c89cab34bb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547963"
---
# <a name="memory-and-paging-performance-rules"></a>Pravidla výkonu paměti a stránkování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pravidla výkonu v kategorii paměti a stránkování identifikují aktivitu stránkování při spuštění profilace, která může ovlivnit výkon a rychlost odezvy aplikace.  
  
|Pravidlo|Popis|  
|-|-|  
|[DA0014: Velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Při průběhu procesu profilace došlo extrémně vysoká míra stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti. Toto pravidlo je vyvoláno, pokud velikost aktivity stránkování překročí horní prahovou hodnotu D0017 pravidla.|  
|[DA0017: Vysoké míry stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Během procesu profilace došlo poměrně vysoké míry stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti.|
