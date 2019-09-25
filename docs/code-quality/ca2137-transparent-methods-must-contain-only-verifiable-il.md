---
title: 'CA2137: Transparentní metody musí obsahovat pouze ověřitelné IL'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ae8f507f17a1c64cb9fdfc5872ffa22e3c0f170
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232235"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Transparentní metody musí obsahovat pouze ověřitelné IL

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Metoda obsahuje kód, který nelze ověřit, nebo vrací typ odkazem.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo je vyvoláno při pokusech transparentního kódu zabezpečení spustit jazyk MSIL (Microsoft Intermediate Language), který nelze ověřit. Pravidlo však neobsahuje úplný ověřovatel jazyka IL a místo toho k zachycení většiny porušení ověření jazyka MSIL používá heuristiky.

Chcete-li mít jistotu, že váš kód obsahuje pouze ověřitelný jazyk MSIL, spusťte [Nástroj Peverify. exe (Nástroj PEVerify nástroj)](/dotnet/framework/tools/peverify-exe-peverify-tool) v sestavení. Spusťte nástroj PEverify s parametrem **/Transparent** , který omezí výstup pouze na neověřitelné transparentní metody, které by způsobily chybu. Pokud není použita možnost/Transparent, nástroj PEverify také ověřuje kritické metody, které mohou obsahovat neověřitelný kód.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, označte metodu <xref:System.Security.SecurityCriticalAttribute> atributem nebo <xref:System.Security.SecuritySafeCriticalAttribute> nebo odeberte neověřitelný kód.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Metoda v tomto příkladu používá neověřitelný kód a měla by být označena <xref:System.Security.SecurityCriticalAttribute> atributem or. <xref:System.Security.SecuritySafeCriticalAttribute>

[!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]