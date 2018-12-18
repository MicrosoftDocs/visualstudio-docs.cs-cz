---
title: 'CA2119: Zapečeťte metody, které vyhovují privátním rozhraním'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: aa207e85bcb7054b1a7b91ac8dd29ff45fe1091a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550593"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Zapečeťte metody, které vyhovují privátním rozhraním

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Odvoditelný veřejný typ poskytuje implementaci přepisovatelné metody `internal` (`Friend` v jazyce Visual Basic) rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Metody rozhraní mít přístupnost public, což není možné změnit implementujícího typu. Vnitřní rozhraní vytvoří kontrakt, který není zamýšlena k implementaci mimo sestavení, který definuje rozhraní. Veřejný typ, který implementuje metodu pomocí interní rozhraní `virtual` (`Overridable` v jazyce Visual Basic) umožňuje Modifikátor metody, která se dá přepsat odvozený typ, který se nachází mimo sestavení. Pokud druhý typ v sestavení volá metodu a očekává, že pouze interní smlouvy, chování může být ohrožené, když místo toho se zpracovává přepsané metody v mimo sestavení. Tím se vytvoří ohrožení zabezpečení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zabránit metody přepsání mimo sestavení pomocí jedné z následujících akcí:

- Ujistěte se, že deklarující typ `sealed` (`NotInheritable` v jazyce Visual Basic).

- Změňte přístupnost deklarující typ, který má `internal` (`Friend` v jazyce Visual Basic).

- Odebrání všech veřejných konstruktorů deklarujícího typu.

- Implementace metody bez použití `virtual` modifikátor.

- Explicitně implementujte metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud po pečlivou revizi, neexistují žádné problémy se zabezpečením, která může být zneužitelné, pokud je přepsána metoda mimo sestavení.

## <a name="example-1"></a>Příklad 1
 Následující příklad ukazuje typ, `BaseImplementation`, který porušuje tato pravidla.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Příklad 2
 Následující příklad využívá virtuální metoda provádění předchozího příkladu.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Viz také:

- [Rozhraní](/dotnet/csharp/programming-guide/interfaces/index)
- [Rozhraní](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)