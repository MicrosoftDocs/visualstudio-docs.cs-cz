---
title: 'CA1308: Normalizujte řetězce na velká písmena'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c33f4b0b55728d659c34e0ffc8723f555a6d074d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234916"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizujte řetězce na velká písmena

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Operace normalizuje řetězec na malá písmena.

## <a name="rule-description"></a>Popis pravidla
Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků, když se převede na malá písmena, nemůže vytvořit zpáteční cestu. Aby bylo možné provést operaci round trip pro převod znaků z jednoho národního prostředí do jiného národního prostředí, které představuje data znaků odlišně, a pak pro přesné načtení původních znaků z převedených znaků.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Změňte operace, které převádějí řetězce na malá písmena, aby byly řetězce převedeny na velká písmena. Například změňte `String.ToLower(CultureInfo.InvariantCulture)` na `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud neprovádíte rozhodnutí zabezpečení na základě výsledku (například při zobrazení v uživatelském rozhraní), je bezpečné potlačit zprávu s upozorněním.

## <a name="see-also"></a>Viz také:
[Upozornění globalizace](../code-quality/globalization-warnings.md)