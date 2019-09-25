---
title: 'CA2134: Metody musí při přepisování základních metod zachovávat konzistentní transparentnost'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 517588826983613c71a74296914b1dfeb3eaa2b4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253319"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody musí při přepisování základních metod zachovávat konzistentní transparentnost

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Toto pravidlo je vyvoláno, je- <xref:System.Security.SecurityCriticalAttribute> li metoda označena s přepsáním metody, která <xref:System.Security.SecuritySafeCriticalAttribute>je průhledná nebo označena atributem. Pravidlo se aktivuje také v případě, že metoda, která je průhledná <xref:System.Security.SecuritySafeCriticalAttribute> nebo označená s přepsáním metody, <xref:System.Security.SecurityCriticalAttribute>která je označena atributem.

Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo je vyvoláno při pokusech o změnu přístupnosti zabezpečení metody v rámci řetězce dědičnosti. Například pokud je virtuální metoda v základní třídě transparentní nebo bezpečná, pak musí být odvozená třída popsána transparentní nebo bezpečnou metodou. Naopak, pokud je virtuální z hlediska zabezpečení kritická, musí odvozená třída tuto třídu přepsat metodou kritické pro zabezpečení. Stejné pravidlo platí pro implementaci metod rozhraní.

Pravidla transparentnosti jsou vynutila, pokud je kód zkompilován kompilátorem JIT namísto za běhu, takže výpočet transparentnosti nemá informace o dynamickém typu. Proto je možné výsledek výpočtu transparentnosti určit výhradně ze statických typů, které jsou kompilovány JIT, bez ohledu na dynamický typ.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte transparentnost metody, která přepisuje virtuální metodu nebo implementuje rozhraní, aby odpovídala průhlednosti metody Virtual nebo rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění z tohoto pravidla Porušení tohoto pravidla vyplývají z doby <xref:System.TypeLoadException> běhu pro sestavení, která používají transparentnost úrovně 2.

## <a name="examples"></a>Příklady

### <a name="code"></a>Kód
[!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Viz také:
[Kód transparentní pro zabezpečení, úroveň 2](/dotnet/framework/misc/security-transparent-code-level-2)