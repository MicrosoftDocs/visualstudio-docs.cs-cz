---
title: 'Kurz 3: vytvoření porovnávací hry'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579702"
---
# <a name="tutorial-3-create-a-matching-game"></a>Kurz 3: vytvoření porovnávací hry

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon.

> [!NOTE]
> Tento kurz se zabývá C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úlohami:

- Uložení objektů, jako jsou ikony, do <xref:System.Collections.Generic.List%601> objektu.

- Použijte `foreach` smyčku v jazyce C# nebo `For Each` smyčku v Visual Basic k iterování položek v seznamu.

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

Až skončíte, aplikace by měla vypadat podobně jako na následujícím obrázku:

![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidáním `TableLayoutPanel` ovládacího prvku, který zajistí správné zarovnání ovládacích prvků.|
|[Krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete- `Random` `List` li vytvořit seznam ikon, přidejte objekt a objekt.|
|[Krok 3: Přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony náhodně `Label` ovládacím prvkům, aby se každá hra lišila.|
|[Krok 4: Přidání obslužné rutiny události Click ke každému popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte `Click` obslužnou rutinu události, která změní barvu popisku, který je na něj kliknuto.|
|[Krok 5: Přidání odkazů popisků](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: Zachování dvojic ve viditelném stavu](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidání metody k ověření, jestli hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidejte `CheckForWinner()` metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušení dalších funkcí](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|

K dispozici jsou také skvělé a bezplatné studijní materiály pro video. Další informace o programování v jazyce C# najdete v tématu [základy jazyka c#: vývoj pro naprostou začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Pokud chcete začít s kurzem, začněte v **[kroku 1: Vytvořte projekt a přidejte tabulku do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Viz také

* [Další kurzy C#](/visualstudio/get-started/csharp/)
* [Kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [Kurzy C++](/cpp/get-started/tutorial-console-cpp)
