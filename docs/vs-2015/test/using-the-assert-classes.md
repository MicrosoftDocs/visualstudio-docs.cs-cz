---
title: Používání tříd Assert | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657139"
---
# <a name="using-the-assert-classes"></a>Používání tříd Assert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro ověření konkrétních funkcí použijte třídy Assert oboru názvů UnitTestingFramework. Metoda testování částí vykonává kód metody v kódu vývoje, ale oznamuje správnost chování kódu pouze v případě, že zahrnete příkazy Assert.

## <a name="kinds-of-asserts"></a>Druhy kontrolních výrazů
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>Obor názvů poskytuje několik druhů kontrolních tříd:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 V testovací metodě můžete volat libovolný počet metod třídy Assert, jako je například Assert. AreEqual (). Třída Assert má mnoho metod, ze kterých si můžete vybrat, a mnohé z těchto metod mají několik přetížení.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Pomocí třídy CollectionAssert můžete porovnat kolekce objektů a ověřit stav jedné nebo více kolekcí.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Pro porovnání řetězců použijte třídu StringAssert. Tato třída obsahuje řadu užitečných metod, jako je například StringAssert. Contains, StringAssert. matchs a StringAssert. StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 Výjimka AssertFailedException je vyvolána pokaždé, když se test nezdařil. Test se nezdařil, pokud vyprší časový limit, vyvolá neočekávanou výjimku nebo obsahuje příkaz kontrolního výrazu, který vytváří výsledek neúspěchu.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 AssertInconclusiveException je vyvolána pokaždé, když test vygeneruje výsledek neprůkazné. Obvykle přidáte Assert. neprůkazný příkaz do testu, na kterém stále pracujete, abyste označili, že ještě není připravený ke spuštění.

> [!NOTE]
> Alternativní strategie by měla označit test, který není připravený ke spuštění s atributem Ignore. To však má nevýhodu, že nemůžete jednoduše generovat sestavu pro počet testů, které jste nastavili k implementaci.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Pokud zapíšete novou třídu výjimky kontrolního výrazu, která má tuto třídu dědit ze základní třídy UnitTestAssertException, zjednoduší identifikaci výjimky jako selhání kontrolního výrazu namísto neočekávané výjimky vyvolané z vašeho testu nebo produkčního kódu.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Upraví testovací metodu s atributem ExpectedExceptionAttribute, pokud chcete, aby metoda testu ověřila, že výjimka, kterou očekáváte vyvolat metodou v kódu vývoje, je ve skutečnosti vyvolána v této metodě.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>[Vytváření a spouštění testů jednotek pro existující kód](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
