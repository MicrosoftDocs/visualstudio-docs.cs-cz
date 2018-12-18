---
title: Mstestu assert třídy a metody
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91198e9b7048b384bf2095840abbd012042025ed
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844253"
---
# <a name="use-assert-classes-for-unit-testing"></a>Používání tříd Assert pro testování částí

Použití třídy Assert <xref:Microsoft.VisualStudio.TestTools.UnitTesting> obor názvů ověření specifické funkce. Metoda testování částí uplatňuje kód metody v kódu aplikace, ale sestavy správnost kódu na chování, pouze pokud zahrnete Assert – příkazy.

## <a name="kinds-of-asserts"></a>Typy z vyhodnotí

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> Obor názvů obsahuje několik druhů tříd Assert.

V testu metodu, můžete volat všechny metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> třídy, jako například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> Třída má mnoho způsobů vybírat a mnoho z metod má několik přetížení.

### <a name="compare-strings-and-collections"></a>Porovnání řetězců a kolekce

Použití <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> třída porovnávání kolekcí objektů, nebo ověřte stav kolekce.

Použití <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> třídy pro porovnání a kontrolu řetězce. Tato třída obsahuje celou řadu užitečných metod, jako například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>, a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Výjimky

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> Vždy, když test se nezdaří, je vyvolána výjimka. Test se nezdaří, pokud vyprší časový limit, neočekávanou výjimku nebo obsahuje příkazu assert, která vytváří **se nezdařilo** výsledek.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> Je vyvolána při každém testu vytvoří výsledek z **Inconclusive**. Obvykle se přidávají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> příkaz k testu, který stále pracujete, k označení ještě není připraven ke spuštění.

> [!NOTE]
> Alternativní strategie je označit test, který není připraven ke spuštění s <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> atribut. To má však nevýhodou, že nelze snadno vygenerovat sestavu na počet testů, které nejsou implementovány.

Pokud napíšete novou, assert – třídy výjimek, způsobem zděděn ze základní třídy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> pro snazší identifikaci výjimky jako chybu assertion místo k neočekávané výjimce v testovacím nebo produkční kódu.

Uspořádání metodu test s <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut, pokud chcete testovací metodu za účelem ověření, že je vyvolána výjimka byste měli být vyvolány metodou v kódu aplikace.

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)