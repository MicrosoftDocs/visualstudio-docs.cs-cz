---
title: 'CA2144: Transparentní kód by neměl načítat sestavení z bajtových polí'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33edff9b22559799cef4ad7e03058a5eb212182b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232011"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: Transparentní kód by neměl načítat sestavení z bajtových polí

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Transparentní metoda načte sestavení z bajtového pole pomocí jedné z následujících metod:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Popis pravidla
Přezkoumání zabezpečení transparentního kódu není tak důsledné jako přezkoumání zabezpečení kritického kódu, protože transparentní kód nemůže provádět akce citlivé na zabezpečení. Sestavení, která jsou načtena z pole bajtů, nemusí být v transparentním kódu zaznamenána a takové pole bajtů může obsahovat kritický nebo důležitější bezpečně kritický kód, který musí být auditován. Transparentní kód proto nesmí načítat sestavení z bajtového pole.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, označte metodu, která načítá sestavení s <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributem nebo.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Pravidlo je aktivováno v následujícím kódu, protože transparentní metoda načte sestavení z bajtového pole.

[!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]