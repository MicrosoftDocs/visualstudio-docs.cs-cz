---
title: Třídy a metody assert MSTest
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c36916c79bd783ed2c6ce960b068e85478b9971d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592045"
---
# <a name="use-assert-classes-for-unit-testing"></a>Použít assert třídy pro testování částí

Pomocí tříd Assert <xref:Microsoft.VisualStudio.TestTools.UnitTesting> oboru názvů ověřte konkrétní funkce. Metoda testování částí vykonává kód metody v kódu vaší aplikace, ale hlásí správnost chování kódu pouze v případě, že zahrnete Assert příkazy.

## <a name="kinds-of-asserts"></a>Druhy nepodmíněných výrazů

Obor <xref:Microsoft.VisualStudio.TestTools.UnitTesting> názvů poskytuje několik druhů Assert tříd.

V testovací metodě můžete volat libovolné <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> metody třídy, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. Třída <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> má mnoho metod na výběr a mnoho metod má několik přetížení.

### <a name="compare-strings-and-collections"></a>Porovnání řetězců a kolekcí

Pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> třídy můžete porovnat kolekce objektů nebo ověřit stav kolekce.

Pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> třídy porovnat a zkoumat řetězce. Tato třída obsahuje řadu užitečných metod, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Výjimky

Výjimka <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> je vyvolána vždy, když se nezdaří test. Test se nezdaří, pokud časový mzda, vyvolá neočekávanou výjimku nebo obsahuje příkaz assert, který vytváří **neúspěšný** výsledek.

Je <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> vyvolána vždy, když test vede k výsledku **Neprůkazné**. Obvykle přidáte příkaz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> do testu, na kterém stále pracujete, což znamená, že ještě není připraven ke spuštění.

> [!NOTE]
> Alternativní strategie je označit test, který není připraven <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> ke spuštění s atributem. To má však nevýhodu, že nelze snadno vygenerovat sestavu o počtu testů, které nejsou implementovány.

Pokud napíšete novou třídu výjimky <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> assert, dědíte ze základní třídy, abyste usnadnili identifikaci výjimky jako selhání kontrolního výrazu namísto neočekávané výjimky vyženou z testovacího nebo produkčního kódu.

Chcete-li ověřit, že výjimka, kterou očekáváte, že bude vyvolána <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodou v kódu aplikace je skutečně vyvolána, použijte metodu.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
