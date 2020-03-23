---
title: 'Tutorial 3: Vytvoření odpovídající hry'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619c21f4878f2e421ee5ac5ea76a68cd6e6bc337
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579702"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Vytvoření odpovídající hry

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon.

> [!NOTE]
> Tento kurz zahrnuje c# a visual basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úkoly:

- Ukládejte objekty, například ikony, do objektu. <xref:System.Collections.Generic.List%601>

- Použijte `foreach` smyčku v `For Each` jazyce C# nebo smyčku v jazyce Visual Basic k iterátu prostřednictvím položek v seznamu.

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

Po dokončení by aplikace měla vypadat podobně jako na následujícím obrázku:

![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu `TableLayoutPanel` a přidáním ovládacího prvku, aby byly ovládací prvky správně zarovnány.|
|[Krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete-li vytvořit seznam ikon, přidejte `Random` objekt a `List` objekt.|
|[Krok 3: Přiřazení náhodné ikony ke každému štítku](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony `Label` náhodně k ovládacím prvkům, takže každá hra je odlišná.|
|[Krok 4: Přidání obslužné rutiny události kliknutí ke každému popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte `Click` obslužnou rutinu události, která změní barvu popisku, na který klepnete.|
|[Krok 5: Přidání odkazů na popisky](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: Zachovat viditelné páry](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu k ověření, zda hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidejte `CheckForWinner()` metodu k ověření, zda hráč vyhrál.|
|[Krok 9: Vyzkoušejte další funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|

K dispozici jsou také skvělé, bezplatné výukové materiály pro video. Další informace o programování v jazyce C#, viz [Základy jazyka C#: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual Basic najdete v [tématu Základy jazyka: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Chcete-li zahájit kurz, začněte krokem **[1: Vytvořte projekt a přidejte tabulku do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Viz také

* [Další výukové programy pro C#](/visualstudio/get-started/csharp/)
* [Výukové programy jazyka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Výukové programy pro C++](/cpp/get-started/tutorial-console-cpp)
