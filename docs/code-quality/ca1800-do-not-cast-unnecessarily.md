---
title: 'CA1800: Nepřetypujte zbytečně'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a1db0f421f72e5b63b14c95a706b738bea1a4174
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550515"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nepřetypujte zbytečně

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
Metoda provádí duplicitní přetypování na jednom z jeho argumenty nebo místní proměnné.

Pro dokončení analýzy tímto pravidlem testované sestavení musí být sestaveny s použitím informací o ladění a přidružené programového souboru databáze (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. Pro explicitní přetypování. duplicitní operace uložení výsledku přetypování do místní proměnné a používat místní proměnnou místo operací duplicitní přetypování.

Pokud jazyka C# `is` operátor se používá k ověření, zda přetypování proběhne úspěšně, před provedením skutečné přetypování, vezměte v úvahu bude testování výsledku `as` operátor místo toho. Funkce bez implicitní přetypování operace prováděné `is` operátor. Nebo v jazyce C# 7.0 nebo novější, použijte `is` operátor s [porovnávání vzorů](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) kontrolu převodu typu a přetypovat výraz, který má proměnnou daného typu v jednom kroku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, upravte implementace metody, chcete-li minimalizovat počet operací přetypování.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné, můžete potlačit upozornění tohoto pravidla nebo ignorovat pravidlo úplně, pokud výkon není žádný problém.

## <a name="examples"></a>Příklady
 Následující příklad ukazuje metodu, která porušuje pravidlo pomocí jazyka C# `is` operátor. Druhá metoda splňuje pravidlo tak, že nahradíte `is` operátor s testují splnění výsledek `as` operátor, který snižuje počet operací přetypování na iteraci ze dvou do jednoho. Třetí metoda také splňuje pravidlo s použitím `is` s [porovnávání vzorů](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) vytvoření proměnné požadovaného typu, pokud by uspěl převod typů.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 Následující příklad ukazuje metodu, `start_Click`, který má více duplicitních explicitní přetypování, který porušuje pravidla a metodu, `reset_Click`, který splňuje pravidlo uložením přetypování do místní proměnné.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Viz také:

- [jako (referenční dokumentace jazyka C#)](/dotnet/csharp/language-reference/keywords/as)
- [je (referenční dokumentace jazyka C#)](/dotnet/csharp/language-reference/keywords/is)