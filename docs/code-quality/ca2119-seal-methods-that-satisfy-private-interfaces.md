---
title: 'CA2119: Zapečeťte metody, které vyhovují privátním rozhraním'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 84cac2f48112c43805cdd9c12a6a41cf56a8ae72
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232620"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Zapečeťte metody, které vyhovují privátním rozhraním

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Dědičný veřejný typ poskytuje implementaci `internal` přepsatelné metody rozhraní (`Friend` v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
Metody rozhraní mají veřejné přístupnost, které nelze změnit implementací typu. Interní rozhraní vytvoří kontrakt, který není určen pro implementaci mimo sestavení, které definuje rozhraní. Veřejný typ, který implementuje metodu interního rozhraní pomocí `virtual` modifikátoru (`Overridable` in Visual Basic), umožňuje metodu přepsat odvozeným typem, který je mimo sestavení. Pokud druhý typ v definičním sestavení volá metodu a očekává pouze interní kontrakt, chování může být ohroženo, když místo toho je provedena přepsaná metoda v externím sestavení. Tím se vytvoří chyba zabezpečení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zabráníte přepsání metody mimo sestavení pomocí jedné z následujících akcí:

- Proveďte deklaraci typu `sealed` (`NotInheritable` v Visual Basic).

- Změňte přístupnost deklarace typu na `internal` (`Friend` v Visual Basic).

- Odebere všechny veřejné konstruktory z deklarující typ.

- Implementujte metodu bez použití `virtual` modifikátoru.

- Explicitně Implementujte metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění od tohoto pravidla, pokud po pečlivém přezkoumání neexistují žádné problémy se zabezpečením, které by mohly být zneužity, pokud je metoda přepsána mimo sestavení.

## <a name="example-1"></a>Příklad 1
Následující příklad ukazuje typ, `BaseImplementation`, který porušuje toto pravidlo.

[!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
[!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
[!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Příklad 2
Následující příklad zneužije implementaci virtuální metody předchozího příkladu.

[!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
[!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
[!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Viz také:

- [Rozhraní](/dotnet/csharp/programming-guide/interfaces/index)
- [Rozhraní](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)