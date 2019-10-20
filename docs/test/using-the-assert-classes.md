---
title: MSTest, třídy a metody kontrolního výrazu
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 41be3aaa4967e4c5f975b43f7d8fec982f04c9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659724"
---
# <a name="use-assert-classes-for-unit-testing"></a>Použití tříd Assert pro testování částí

Pro ověření konkrétních funkcí použijte třídy Assert oboru názvů <xref:Microsoft.VisualStudio.TestTools.UnitTesting>. Metoda testování částí zpracuje kód metody v kódu vaší aplikace, ale oznámí správnost chování kódu pouze v případě, že zahrnete příkazy Assert.

## <a name="kinds-of-asserts"></a>Druhy kontrolních výrazů

Obor názvů <xref:Microsoft.VisualStudio.TestTools.UnitTesting> poskytuje několik druhů kontrolních tříd.

V testovací metodě můžete volat libovolné metody třídy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. Třída <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> obsahuje mnoho metod, ze kterých si můžete vybrat, přičemž mnoho metod má několik přetížení.

### <a name="compare-strings-and-collections"></a>Porovnávání řetězců a kolekcí

Použijte třídu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> pro porovnání kolekcí objektů nebo pro ověření stavu kolekce.

Pro porovnání a prohlédnutí řetězců použijte třídu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>. Tato třída obsahuje celou řadu užitečných metod, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Výjimky

Výjimka <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> je vyvolána pokaždé, když se test nezdařil. Test se nezdařil, pokud vyprší časový limit, vyvolá neočekávanou výjimku nebo obsahuje příkaz kontrolního výrazu, který vytváří výsledek **neúspěchu** .

@No__t_0 je vyvolána pokaždé, když test vygeneruje výsledek **neprůkazné**. Obvykle přidáte příkaz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> do testu, na kterém stále pracujete, abyste označili, že ještě není připravené ke spuštění.

> [!NOTE]
> Alternativním strategií je označit test, který není připraven ke spuštění s atributem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>. To však má nevýhodu, že nemůžete snadno generovat sestavu pro počet testů, které nejsou implementovány.

Pokud zapíšete novou třídu výjimky kontrolního výrazu, je děděna ze základní třídy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> pro snadnější identifikaci výjimky jako selhání kontrolního výrazu namísto neočekávané výjimky vyvolané z vašeho testovacího nebo produkčního kódu.

Chcete-li ověřit, že je ve skutečnosti vyvolána výjimka, kterou očekáváte k vyvolání metodou v kódu aplikace, použijte metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)