---
title: 'DA0011: nákladný objekt CompareTo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779425"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Náročná metoda CompareTo

|||
|-|-|
|Id pravidla|DA0011|
|Kategorie|Využití .NET Framework|
|Metody profilace|Kontrol<br /><br /> Paměť .NET|
|Zpráva|Funkce CompareTo by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce CompareTo.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>příčina
 Metoda CompareTo typu je nákladné nebo přiděluje paměť.

## <a name="rule-description"></a>Popis pravidla
 Metody CompareTo by měly být efektivní a neměly by přidělovat paměť.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Snižte složitost metody CompareTo.
