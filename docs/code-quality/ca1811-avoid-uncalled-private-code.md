---
title: 'CA1811: Vyhněte se nevolanému privátnímu kódu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233625"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Vyhněte se nevolanému privátnímu kódu

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Soukromý nebo interní člen (na úrovni sestavení) nemá volající v sestavení, není vyvolán modulem CLR (Common Language Runtime) a není vyvolán delegátem. Následující členové nejsou kontrolováni tímto pravidlem:

- Explicitní členy rozhraní.

- Statické konstruktory.

- Konstruktory serializace.

- Metody označené <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> nebo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

- Členy, které jsou popsány.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo může hlásit falešně pozitivní hodnoty, pokud se vstupní body, které nejsou aktuálně identifikovány logikou pravidla. Kompilátor může také generovat nevolající kód do sestavení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, odeberte nevolající kód nebo přidejte kód, který ho volá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění.

## <a name="related-rules"></a>Související pravidla
[CA1812: Vyhněte se nevytváření instancí vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Zkontrolovat nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Odebrat nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)