---
title: Pravidla výkonu paměti a stránkování | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778554"
---
# <a name="memory-and-paging-performance-rules"></a>Pravidla výkonu paměťového a stránkovacího
Pravidla výkonu v kategorii paměti a stránkování identifikují aktivitu stránkování v profilovacím běhu, která může ovlivnit výkon aplikace a odezvu.

|||
|-|-|
|[DA0014: Velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Extrémně vysoká rychlost stránkování aktivní paměti na disk a z disku došlo v průběhu profilování spustit. Rychlost stránkování na této úrovni obvykle ovlivňuje výkon a odezvu aplikace. Zvažte snížení přidělení paměti revistou algoritmů. Může být také třeba zvážit požadavky na paměť vaší aplikace. Zkuste profilování spustit znovu v počítači, který má více paměti. Toto pravidlo je aktivováno, když množství stránkovací aktivity překročí horní prahovou hodnotu pravidla D0017.|
|[DA0017: Vysoké míry stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Relativně vysoká rychlost stránkování aktivní paměti na disk a z disku došlo v průběhu profilování spustit. Rychlost stránkování na této úrovni obvykle ovlivňuje výkon a odezvu aplikace. Zvažte snížení přidělení paměti revistou algoritmů. Může být také třeba zvážit požadavky na paměť vaší aplikace. Zkuste profilování spustit znovu v počítači, který má více paměti.|
