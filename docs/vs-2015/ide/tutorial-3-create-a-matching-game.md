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
ms.openlocfilehash: 1d67e81aa90faa59cf5320293aba9e7d82e3f625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654735"
---
# <a name="tutorial-3-create-a-matching-game"></a>Kurz 3: vytvoření porovnávací hry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto tutoriálu vytvoříte porovnávací hru, ve které hráč musí porovnat dvojice skrytých ikon. Získáte informace o následujících postupech:

- Ukládat objekty, jako jsou ikony, do objektu `List`.

- Použijte smyčku `foreach` v vizuálu C# nebo smyčku `For Each` v Visual Basic k iterování položek v seznamu.

- Udržování přehledu o stavu formuláře pomocí referenčních proměnných

- Sestavení obslužné rutiny události pro reakci na události, které lze použít s více objekty

- Vytvoření časovače, který odpočítává a po spuštění přesně jednou aktivuje událost

  Po absolvování tohoto tutoriálu váš program bude vypadat jako na následujícím obrázku.

  ![Hra, kterou v tomto kurzu vytvoříte](../ide/media/express-finishedgame.png "Express_FinishedGame") Hra, kterou v tomto kurzu vytvoříte

  Pokud si chcete stáhnout dokončenou verzi ukázky, přečtěte si [ukázku s kurzem kompletní porovnávací hru](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> V tomto tutoriálu je zahrnut jazyk Visual C# i jazyk Visual Basic, takže se zaměřte na informace, které jsou specifické pro vámi používaný programovací jazyk.

 Pokud si nevíte rady nebo máte otázky k programování, můžete zveřejnit svůj dotaz na jednom z diskuzních fór MSDN. Viz [Visual Basic Fórum](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) a [vizuální C# Fórum](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral). K dispozici jsou také užitečné bezplatné video výukové materiály. Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v vizuálů C#najdete v tématu [ C# základy: vývoj pro absolutní začátečníky](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvořte projekt a přidejte do svého formuláře tabulku](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Začněte vytvořením projektu a přidáním ovládacího prvku `TableLayoutPanel`, abyste zachovali správné zarovnání ovládacích prvků.|
|[Krok 2: Přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Chcete-li vytvořit seznam ikon, přidejte objekt `Random` a objekt `List`.|
|[Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony](../ide/step-3-assign-a-random-icon-to-each-label.md)|Přiřaďte ikony náhodně ovládacím prvkům `Label`, aby se každá hra lišila.|
|[Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Přidejte obslužnou rutinu události Click, která změní barvu popisku, na který jste klikli.|
|[Krok 5: Přidejte odkazy na jmenovky](../ide/step-5-add-label-references.md)|Přidejte referenční proměnné k udržení přehledu o tom, na jaké popisky jste klikli.|
|[Krok 6: Přidejte časovač](../ide/step-6-add-a-timer.md)|Přidejte do formuláře časovač pro sledování času, který ve hře uběhl.|
|[Krok 7: Uchovejte páry ve viditelném stavu](../ide/step-7-keep-pairs-visible.md)|Ponechte dvojice ikon viditelné, pokud je vybrána odpovídající dvojice.|
|[Krok 8: Přidejte metodu k ověření, zda hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Přidejte `CheckForWinner()` metodu k ověření, zda hráč zvítězil.|
|[Krok 9: Vyzkoušejte jiné funkce](../ide/step-9-try-other-features.md)|Zkuste další funkce, jako je například změna ikon a barev, přidání mřížky a přidání zvuků. Zkuste zvětšit hrací plochu a nastavit časovač.|
