---
title: Ladění LINQ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 081c97bffc062bf2bbc9d24feed13e5e512b8c74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755614"
---
# <a name="debugging-linq"></a>Ladění LINQ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje ladění jazyka integrované dotazu kód (LINQ), s určitými omezeními. Většina funkcí ladění pracuje s příkazy LINQ, včetně krokování, nastavení zarážek a zobrazení výsledků v oknech ladicího programu. Toto téma popisuje hlavní omezení ladění LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Zobrazení výsledků LINQ  
 Můžete zobrazit výsledek příkazu LINQ pomocí datových tipů, okna kukátka a dialogového okna rychlého kukátka. Při použití okna zdroje můžete pozastavíte ukazatel myši na dotazu v okně zdroje a zobrazí se datatip. Můžete zkopírovat proměnnou LINQ a vložte ho do okna kukátka nebo dialogového okna rychlého kukátka.  
  
 V LINQ dotaz není vyhodnocen při vytváření nebo deklaraci, ale pouze v případě, že tento dotaz se použije. Proto dotaz nemá hodnotu, dokud není vyhodnocen. Úplný popis vytváření a vyhodnocování dotazu naleznete v tématu [Úvod do dotazů LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) nebo [zápis svůj první dotaz LINQ](http://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Pokud chcete zobrazit výsledky dotazu, ladicí program ho musí vyhodnotit. Toto implicitní hodnocení, ke kterému dochází při zobrazení výsledku dotazu LINQ v ladicím programu, má některé efekty, které byste měli zvážit:  
  
-   Každé vyhodnocení dotazu trvá určitou dobu. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů opakované hodnocení může způsobit znatelné penalizace.  
  
-   Vyhodnocení dotazu může mít za následek vedlejší účinky, které znamenají změnu hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Pokud chcete zjistit, zda dotaz může být bezpečně zhodnocen bez vedlejších účinků, je třeba pochopit kód, který implementuje dotaz.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Krokování a LINQ  
 Když ladíte kód LINQ, krokování má některé behaviorální rozdíly, které byste měli vědět.  
  
### <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 V dotazech LINQ to SQL je kód predikátu mimo kontrolu ladicího programu. Proto je nelze krokovat s vnořením přistoupit predikovanému kódu. Jakýkoli dotaz, který kompiluje na strom výrazu vytvoří kód, který je mimo kontrolu ladicího programu.  
  
### <a name="stepping-in-visual-basic"></a>Krokování v jazyce Visual Basic  
 Když provádíte krokování pomocí programu Visual Basic a ladicí program zaznamená deklaraci dotazu, nepřikročí deklaraci, ale označí celou deklaraci jako jeden příkaz. K tomuto chování dochází, protože dotaz není vyhodnocen, dokud není volán. Další informace najdete v tématu [Úvod do LINQ v JAZYKU Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Pokud projdete následující ukázkový kód, ladicí program zvýrazní deklaraci dotazu nebo vytvoření dotazu jako jeden příkaz.  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Při následném kroku ladicí program zvýrazní `For Each cur In x`. V dalším kroku se přejde k funkci `MyFunction`. Po průchodu `MyFunction`, bude proveden návrat na `Console.WriteLine(cur.ToSting())`. V žádném bodě ho krokovat kód predikátu v deklaraci dotazu, i když ladicí program daný kód hodnotí.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Nahrazení predikátu za funkci umožňující taktování (Visual Basic)  
 Pokud máte krokovat kód predikátu pro účely ladění, můžete nahradit predikát voláním funkce, která obsahuje původní kód predikátu. Předpokládejme například, že máte tento kód:  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Predikátu kódu můžete přesunout na novou funkci nazvanou `IsEven`:  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 Upravený dotaz volá funkci `IsEven` na každém průchodu přes `items`. Můžete použít okna ladicího programu zda každá položka splňuje zadanou podmínku a krokovat kód v `IsEven`. Predikát v tomto příkladu je poměrně jednoduché. Nicméně pokud máte složitější predikát, který je třeba ladit, tato technika může být velmi užitečné.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Upravit a pokračovat není podporována pro LINQ  
 Upravit a pokračovat nepodporuje změny dotazů LINQ. Je-li přidat, odebrat nebo změníte příkaz LINQ během relace ladění, zobrazí se dialogové okno s oznámením, že tato změna není podporována možností upravit a pokračovat. V tomto okamžiku můžete buď vrátit zpět změny nebo zastavit ladicí relaci a znovu spustit novou relaci s upraveným kódem.  
  
 Kromě toho upravit a pokračovat nepodporuje změnu typu ani hodnoty proměnné, který se používá ve výrazu LINQ. Znovu můžete buď vrátit zpět změny nebo zastavte a restartujte relaci ladění.  
  
 V jazyce C# nelze používat funkce upravit a pokračovat na žádný kód v metodě, která obsahuje dotaz LINQ.  
  
 V jazyce Visual Basic můžete upravit a pokračovat na kód jiný než LINQ, dokonce i v metodě, která obsahuje dotaz LINQ. Můžete přidat nebo odebrat kód před příkazem LINQ i v případě, že změny ovlivní počet řádků v dotazu LINQ. V jazyce Visual Basic prostředí ladění pro kód jiný než LINQ zůstává stejná jako před zavedením LINQ. Nelze změnit, přidat nebo odebrat dotaz LINQ, ale pokud chcete zastavit ladění, aby se změny projevily.  
  
## <a name="see-also"></a>Viz také  
 [Ladění SQL](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Vedlejší efekty a výrazy](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)   
 [Úvod do dotazů LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Úvod do LINQ v JAZYKU Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)



