---
title: 'CA1308: Normalizujte řetězce na velká písmena | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538733"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizujte řetězce na velká písmena
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Operace normalizuje řetězec na malá písmena.

## <a name="rule-description"></a>Popis pravidla
 Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků, když se převede na malá písmena, nemůže vytvořit zpáteční cestu. Aby bylo možné provést operaci round trip pro převod znaků z jednoho národního prostředí do jiného národního prostředí, které představuje data znaků odlišně, a pak pro přesné načtení původních znaků z převedených znaků.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte operace, které převádějí řetězce na malá písmena, aby byly řetězce převedeny na velká písmena. Například změňte `String.ToLower(CultureInfo.InvariantCulture)` na `String.ToUpper(CultureInfo.InvariantCulture)` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud neprovádíte rozhodnutí zabezpečení na základě výsledku (například při zobrazení v uživatelském rozhraní), je bezpečné potlačit zprávu s upozorněním.

## <a name="see-also"></a>Viz také
 [Upozornění globalizace](../code-quality/globalization-warnings.md)
