---
title: Ladění LINQ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8511c3ac9efd79b712680bfe3f9d5611f3c5aa9c
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349423"
---
# <a name="debugging-linq"></a>Ladění LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podporuje ladění jazyka integrované dotazu kód (LINQ), s určitými omezeními. Většina funkcí ladění pracuje s příkazy LINQ, včetně krokování, nastavení zarážek a zobrazení výsledků v oknech ladicího programu. Toto téma popisuje hlavní omezení ladění LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Zobrazení výsledků LINQ  
 Můžete zobrazit výsledek příkazu LINQ pomocí datových tipů, okna kukátka a dialogového okna rychlého kukátka. Při použití okna zdroje můžete pozastavíte ukazatel myši na dotazu v okně zdroje a zobrazí se datatip. Můžete zkopírovat proměnnou LINQ a vložte ho do okna kukátka nebo dialogového okna rychlého kukátka.  
  
 V LINQ dotaz není vyhodnocen při vytváření nebo deklaraci, ale pouze v případě, že tento dotaz se použije. Proto dotaz nemá hodnotu, dokud není vyhodnocen. Úplný popis vytváření a vyhodnocování dotazu naleznete v tématu [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) nebo [zápis svůj první dotaz LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Pokud chcete zobrazit výsledky dotazu, ladicí program ho musí vyhodnotit. Toto implicitní hodnocení, ke kterému dochází při zobrazení výsledku dotazu LINQ v ladicím programu, má některé efekty, které byste měli zvážit:  
  
-   Každé vyhodnocení dotazu trvá určitou dobu. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů opakované hodnocení může způsobit znatelné penalizace.  
  
-   Vyhodnocení dotazu může mít za následek vedlejší účinky, které znamenají změnu hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Pokud chcete zjistit, zda dotaz může být bezpečně zhodnocen bez vedlejších účinků, je třeba pochopit kód, který implementuje dotaz.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Krokování a LINQ  
 Když ladíte kód LINQ, krokování má některé behaviorální rozdíly, které byste měli vědět.  
  
### <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 V dotazech LINQ to SQL je kód predikátu mimo kontrolu ladicího programu. Proto je nelze krokovat s vnořením přistoupit predikovanému kódu. Jakýkoli dotaz, který kompiluje na strom výrazu vytvoří kód, který je mimo kontrolu ladicího programu.  
  
### <a name="stepping-in-visual-basic"></a>Krokování v jazyce Visual Basic  
 Když provádíte krokování pomocí programu Visual Basic a ladicí program zaznamená deklaraci dotazu, nepřikročí deklaraci, ale označí celou deklaraci jako jeden příkaz. K tomuto chování dochází, protože dotaz není vyhodnocen, dokud není volán. Další informace najdete v tématu [Úvod do LINQ v JAZYKU Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Pokud projdete následující ukázkový kód, ladicí program zvýrazní deklaraci dotazu nebo vytvoření dotazu jako jeden příkaz.  
  
```vb
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
  
```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Predikátu kódu můžete přesunout na novou funkci nazvanou `IsEven`:  
  
```vb
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
 Upravit a pokračovat podporuje změny dotazů LINQ s omezeními. Podrobnosti najdete v tématu [EnC nepodporuje změny](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>Viz také

- [Ladění SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)
- [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Úvod do LINQ v JAZYKU Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
