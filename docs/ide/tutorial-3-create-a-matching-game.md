---
title: 'Kurz 3: Vytvořit porovnávací hru'
ms.date: 11/04/2016
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8fafd46561b6a3628989b675b14c493b60da6fe
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118702"
---
# <a name="tutorial-3-create-a-matching-game"></a>Kurz 3: Vytvořit porovnávací hru

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon. Získáte informace o následujících postupech:

- Uložení objektů, jako jsou ikony, do <xref:System.Collections.Generic.List%601> objektu.

- Použijte smyčku v vizuálu C# nebo `For Each` smyčku v Visual Basic k iterování položek v seznamu. `foreach`

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

Po dokončení tohoto kurzu bude program vypadat jako na následujícím obrázku:

![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Odkazy na kurz

Pokud si chcete stáhnout dokončenou verzi ukázky, přečtěte si [ukázku s kurzem kompletní porovnávací hru](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> V tomto tutoriálu je zahrnut jazyk Visual C# i jazyk Visual Basic, takže se zaměřte na informace, které jsou specifické pro vámi používaný programovací jazyk.

Pokud si nevíte rady nebo máte otázky k programování, můžete zveřejnit svůj dotaz na jednom z diskuzních fór MSDN. Viz [Visual Basic Fórum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) a [vizuální C# Fórum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral). K dispozici jsou také užitečné bezplatné video výukové materiály. Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: Vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v vizuálů C#najdete v tématu [ C# základy: Vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidáním `TableLayoutPanel` ovládacího prvku, který zajistí správné zarovnání ovládacích prvků.|
|[Krok 2: Přidat náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete-li vytvořit seznam `List` ikon, přidejte objektaobjekt.`Random`|
|[Krok 3: Přiřadit náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony náhodně `Label` ovládacím prvkům, aby se každá hra lišila.|
|[Krok 4: Přidat obslužnou rutinu události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte obslužnou rutinu události, která změní barvu popisku, který je na něj kliknuto. `Click`|
|[Krok 5: Přidat odkazy popisků](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidat časovač](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: Zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu pro ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|`CheckForWinner()` Přidejte metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušet jiné funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|
