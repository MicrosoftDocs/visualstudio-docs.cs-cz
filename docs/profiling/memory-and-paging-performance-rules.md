---
title: Pravidla výkonu paměti a stránkování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f491ee766b2f17e14a8d13cc189018adea84903f
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778554"
---
# <a name="memory-and-paging-performance-rules"></a>Pravidla výkonu paměti a stránkování
Pravidla výkonu v kategorii paměti a stránkování identifikují aktivitu stránkování při spuštění profilace, která může ovlivnit výkon a rychlost odezvy aplikace.

|||
|-|-|
|[DA0014: Velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Při průběhu procesu profilace došlo extrémně vysoká míra stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti. Toto pravidlo je vyvoláno, pokud velikost aktivity stránkování překročí horní prahovou hodnotu D0017 pravidla.|
|[DA0017: Vysoké míry stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Během procesu profilace došlo poměrně vysoké míry stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti.|
