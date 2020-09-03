---
title: 'Kurz 3: vytvoření vyhovující hry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299858"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutoriál 3: Vytvoření hry s hledáním shody
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon. Získáte informace o těchto tématech:

- Uložení objektů, jako jsou ikony, do `List` objektu.

- Použijte `foreach` smyčku v jazyce Visual C# nebo `For Each` smyčku v Visual Basic k iterování položek v seznamu.

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

  Po absolvování tohoto tutoriálu váš program bude vypadat jako na následujícím obrázku.

  ![Hra, kterou v tomto kurzu vytvoříte](../ide/media/express-finishedgame.png "Express_FinishedGame") Hra, kterou v tomto kurzu vytvoříte

> [!NOTE]
> V tomto tutoriálu je zahrnut jazyk Visual C# i jazyk Visual Basic, takže se zaměřte na informace, které jsou specifické pro vámi používaný programovací jazyk.

 Pokud si nevíte rady nebo máte otázky k programování, můžete zveřejnit svůj dotaz na jednom z diskuzních fór MSDN. Viz Fórum [Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) Fórum [Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home). K dispozici jsou také užitečné bezplatné video výukové materiály. Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual C# najdete v tématu [základy jazyka C#: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidáním `TableLayoutPanel` ovládacího prvku, který zajistí správné zarovnání ovládacích prvků.|
|[Krok 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete- `Random` `List` li vytvořit seznam ikon, přidejte objekt a objekt.|
|[Krok 3: přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony náhodně `Label` ovládacím prvkům, aby se každá hra lišila.|
|[Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte obslužnou rutinu události Click, která změní barvu popisku, na který jste klikli.|
|[Krok 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu k ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidejte `CheckForWinner()` metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušejte jiné funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|
