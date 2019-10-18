---
title: 'Kurz 3: vytvoření porovnávací hry'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5161f81aaf3edf654a5979f6226449bc52604167
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516578"
---
# <a name="tutorial-3-create-a-matching-game"></a>Kurz 3: vytvoření porovnávací hry

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon.

> [!NOTE]
> Tento kurz se zabývá C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úlohami:

- Ukládat objekty, jako jsou ikony, do objektu <xref:System.Collections.Generic.List%601>.

- Pomocí smyčky `foreach` v C# nebo v Visual Basic `For Each` v rámci iterace položky v seznamu.

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

Až skončíte, aplikace by měla vypadat podobně jako na následujícím obrázku:

![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Název|Popis|
|-----------|-----------------|
|[Krok 1: vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidáním ovládacího prvku `TableLayoutPanel`, abyste zachovali správné zarovnání ovládacích prvků.|
|[Krok 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete-li vytvořit seznam ikon, přidejte objekt `Random` a objekt `List`.|
|[Krok 3: přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony náhodně ovládacím prvkům `Label`, aby se každá hra lišila.|
|[Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte obslužnou rutinu události `Click`, která změní barvu popisku, který je na něj kliknuto.|
|[Krok 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu k ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidejte `CheckForWinner()` metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušejte jiné funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|

K dispozici jsou také skvělé a bezplatné studijní materiály pro video. Další informace o programování v C#nástroji najdete v tématu [ C# základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Pokud chcete začít s kurzem, začněte v **[kroku 1: Vytvořte projekt a přidejte tabulku do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** .

## <a name="see-also"></a>Viz také:

* [Další C# kurzy](/visualstudio/get-started/csharp/)
* [Kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++výuka](/cpp/get-started/tutorial-console-cpp)
