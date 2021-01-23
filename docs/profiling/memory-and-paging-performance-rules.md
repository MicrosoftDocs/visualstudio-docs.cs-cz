---
title: Pravidla výkonu paměti a stránkování | Microsoft Docs
description: Přečtěte si, jak pravidla výkonu v kategorii paměti a stránkování identifikují aktivitu stránkování při spuštění profilace, která může ovlivnit výkon a rychlost odezvy aplikace.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1cddda12fbb67f9b604186e754146558cdd62ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720602"
---
# <a name="memory-and-paging-performance-rules"></a>Pravidla výkonu paměti a stránkování
Pravidla výkonu v kategorii paměti a stránkování identifikují aktivitu stránkování při spuštění profilace, která může ovlivnit výkon a rychlost odezvy aplikace.

|Pravidlo|Popis|
|-|-|
|[DA0014: Velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Při průběhu procesu profilace došlo extrémně vysoká míra stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti. Toto pravidlo je vyvoláno, pokud velikost aktivity stránkování překročí horní prahovou hodnotu D0017 pravidla.|
|[DA0017: Vysoké míry stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Během procesu profilace došlo poměrně vysoké míry stránkování aktivní paměti na disk a z disku. Rychlosti stránkování na této úrovni obvykle ovlivňují výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. Zkuste znovu spustit profilaci v počítači, který má více paměti.|
