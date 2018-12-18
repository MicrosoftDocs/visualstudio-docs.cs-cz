---
title: 'Tutoriál 3: Vytvoření odpovídající her'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d77bfad86024cf95ce1649498ddda5d1450a1c33
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672012"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutoriál 3: Vytvoření odpovídající her

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon. Získáte informace o následujících postupech:

-   Store objektů, například ikon, v <xref:System.Collections.Generic.List%601> objektu.

-   Použití `foreach` smyčky v jazyce Visual C# nebo `For Each` smyčky v jazyce Visual Basic k iterování položek v seznamu.

-   Udržování přehledu o stavu formuláře pomocí referenčních proměnných

-   Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

-   Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

Po dokončení tohoto kurzu, váš program bude vypadat jako na následujícím obrázku:

![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Kurz odkazy

Chcete-li stáhnout úplnou verzi vzorku, přečtěte si téma [kompletní odpovídající her ukázkový kurz](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> V tomto tutoriálu je zahrnut jazyk Visual C# i jazyk Visual Basic, takže se zaměřte na informace, které jsou specifické pro vámi používaný programovací jazyk.

Pokud si nevíte rady nebo máte otázky k programování, můžete zveřejnit svůj dotaz na jednom z diskuzních fór MSDN. Zobrazit [fórum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) a [fórum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral). K dispozici jsou také užitečné bezplatné video výukové materiály. Další informace o programování v jazyce Visual Basic najdete v tématu [základy jazyka Visual Basic: vývoj pro naprosté začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual C# najdete v tématu [Základy C#: vývoj pro naprosté začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvořte projekt a přidejte do svého formuláře tabulku](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidání `TableLayoutPanel` ovládacího prvku, aby ovládací prvky byly správně zarovnány.|
|[Krok 2: Přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Přidat `Random` objektu a `List` objekt k vytvoření seznamu ikon.|
|[Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony](../ide/step-3-assign-a-random-icon-to-each-label.md)|Náhodně přiřaďte ikony `Label` ovládací prvky, aby každé hra se liší.|
|[Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidat `Click` obslužná rutina události, která změní barvu popisku, který po kliknutí na.|
|[Krok 5: Přidejte odkazy na jmenovky](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidejte časovač](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: Páry ve viditelném stavu](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu k ověření, zda hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidat `CheckForWinner()` metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušejte jiné funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|
