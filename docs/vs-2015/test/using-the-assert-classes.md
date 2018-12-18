---
title: Používání tříd Assert | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6775f7ea22bab5d210eb4e2993e81bd4a9587560
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208309"
---
# <a name="using-the-assert-classes"></a>Používání tříd Assert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Používání tříd Assert oboru názvů UnitTestingFramework ověření konkrétní funkce. Metodu testovací jednotky uplatňuje kód metody v kódu vývoje, ale sestavy správnosti kódu chování pouze v případě, že zahrnete Assert – příkazy.  
  
## <a name="kinds-of-asserts"></a>Typy z nepodmíněné výrazy  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Obor názvů obsahuje několik typů tříd Assert:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 V testovací metodě může volat libovolný počet metody Assert třídy, jako je například Assert.AreEqual(). Třída Assert má vybírat z mnoha způsobů a řada z těchto metod má několik přetížení.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Použití třídy CollectionAssert porovnávání kolekcí objektů a ověřte stav jednoho nebo více kolekcí.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Třída StringAssert slouží k porovnání řetězců. Tato třída obsahuje celou řadu užitečných metod, jako je například StringAssert.Contains StringAssert.Matches a StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Pokaždé, když se test nezdaří, je vyvolána výjimka AssertFailedException. Test selže, pokud vyprší časový limit, dojde k neočekávané výjimce nebo obsahuje kontrolní příkaz, který vytváří jako výsledek selhání.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 Pokaždé, když se test vytváří výsledek neprůkazné, je vyvolána AssertInconclusiveException. Obvykle přidáte příkazem Assert.Inconclusive test, který se stále pracujete označující, že ještě není připraven ke spuštění.  
  
> [!NOTE]
>  Alternativní strategií je označit test, který není připraven ke spuštění s atributem ignorovat. Má to ale nevýhodou, že nelze snadno vygenerujete sestavu pro počet testů, že ještě zbývá k implementaci.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Pokud píšete novou třídu výjimek Assert, s této třídy dědit ze základní třídy UnitTestAssertException usnadňuje identifikaci výjimky jako selhání kontrolního výrazu místo Neočekávaná výjimka vyvolána v testovacím nebo produkčním kódu.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Testovací metodu s atributem ExpectedExceptionAttribute uspořádání, pokud chcete testovací metodu za účelem ověření, že dojde k výjimce, které byste měli být vyvolány metodou ve vašem kódu vývoje skutečně se v této metodě.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Vytváření a spouštění testů jednotek pro existující kód](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)



