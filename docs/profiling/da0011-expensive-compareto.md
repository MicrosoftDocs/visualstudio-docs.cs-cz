---
title: DA0011 – nákladný objekt CompareTo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aef8135e48b07946803832266ed9dff9e843d3ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916818"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Náročná funkce CompareTo

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0011|
|Kategorie|Využití .NET Framework|
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|
|Zpráva|Funkce CompareTo by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce CompareTo.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>Příčina
 Metoda CompareTo typu je nákladné nebo přiděluje paměť.

## <a name="rule-description"></a>Popis pravidla
 Metody CompareTo by měly být efektivní a neměly by přidělovat paměť.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Snižte složitost metody CompareTo.
