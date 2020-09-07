---
title: Ladění LINQ | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 146519b33be19da1103aed958e42ec5ffaee8bd0
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509767"
---
# <a name="debugging-linq"></a>Ladění LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podporuje ladění kódu LINQ (Language Integrated Query) s některými omezeními. Většina funkcí ladění funguje s příkazy LINQ, včetně krokování, nastavení zarážek a zobrazení výsledků v oknech ladicího programu. Toto téma popisuje hlavní omezení pro ladění jazyka LINQ.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> Zobrazení výsledků LINQ
 Výsledek příkazu LINQ lze zobrazit pomocí tipů, okno Kukátko a dialogového okna QuickWatch. Když použijete zdrojové okno, můžete pozastavit ukazatel na dotaz v okně zdroje a zobrazí se DataTip. Můžete zkopírovat proměnnou LINQ a vložit ji do dialogového okna okno Kukátko nebo QuickWatch.

 V LINQ není dotaz vyhodnocen, když je vytvořen nebo deklarován, ale pouze v případě, že je dotaz použit. Proto dotaz nemá hodnotu, dokud není vyhodnocen. Úplný popis vytváření a vyhodnocení dotazů naleznete v tématu [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) nebo [zápis prvního dotazu LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Chcete-li zobrazit výsledek dotazu, musí ho ladicí program vyhodnotit. Toto implicitní vyhodnocení, ke kterému dochází při zobrazení výsledku dotazu LINQ v ladicím programu, má některé efekty, které byste měli zvážit:

- Každé vyhodnocení dotazu trvá čas. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů může opakované vyhodnocení vést k výraznému snížení výkonu.

- Vyhodnocení dotazu může mít vedlejší účinky, což jsou změny hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Chcete-li zjistit, zda může být dotaz bezpečně vyhodnocován bez vedlejších účinků, je nutné pochopit kód, který implementuje dotaz.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Krokování a LINQ
 Když ladíte kód LINQ, krokování obsahuje některé rozdíly v chování, které byste měli znát.

### <a name="linq-to-sql"></a>Technologie LINQ to SQL
 V LINQ to SQL dotazy je kód predikátu mimo ovládací prvek ladicího programu. Proto nemůžete Krokovat s kódem predikátu. Jakýkoli dotaz, který zkompiluje do stromu výrazů vytvoří kód, který je mimo ovládací prvek ladicího programu.

### <a name="stepping-in-visual-basic"></a>Krokování v Visual Basic
 Když procházíte Visual Basic program a ladicí program narazí na deklaraci dotazu, neprovede krok do deklarace, ale zvýrazní celou deklaraci jako jeden příkaz. K tomuto chování dochází, protože dotaz není vyhodnocen, dokud není volán. Další informace najdete v tématu [Úvod do LINQ v Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Pokud provedete následující příklad kódu, ladicí program zvýrazní deklaraci dotazu nebo vytvoření dotazu jako jediný příkaz.

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

 V případě opětovného kroku ladicí program zvýrazní `For Each cur In x` . V dalším kroku se tento postup zavolá do funkce `MyFunction` . Po krokování `MyFunction` přejde zpět na `Console.WriteLine(cur.ToSting())` . V žádném bodě krok projde kódem predikátu v deklaraci dotazu, i když ladicí program vyhodnotí tento kód.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Nahrazení predikátu funkcí, která umožňuje krokování (Visual Basic)
 Pokud je nutné krokovat kód predikátu pro účely ladění, můžete nahradit predikát voláním funkce, která obsahuje původní kód predikátu. Předpokládejme například, že máte tento kód:

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Můžete přesunout kód predikátu do nové funkce s názvem `IsEven` :

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

 Revidovaný dotaz volá funkci `IsEven` při každém průchodu pomocí `items` . Okna ladicího programu můžete použít k zobrazení, zda každá položka splňuje zadanou podmínku, a můžete krokovat kód v `IsEven` . Predikát v tomto příkladu je poměrně jednoduchý. Nicméně pokud máte složitější predikát, který je třeba ladit, tato technika může být velmi užitečná.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Úpravy a pokračování nejsou podporovány pro LINQ
 Upravit a pokračovat podporuje změny v dotazech LINQ s omezeními. Podrobnosti najdete v článku [podporované změny v ENC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) .

## <a name="see-also"></a>Viz také

- [Ladění SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)
- [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Představení technologie LINQ v jazyce Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
