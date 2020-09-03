---
title: 'Krok 5: Přidání odkazů na štítky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671742"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidejte odkazy na jmenovky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program potřebuje udržovat přehled o tom, který ovládací prvek popisku hráč zvolil. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Váš program teď bude sledovat, který ovládací prvek popisek je vybraný jako první a který se volí za druhým pomocí *referenčních proměnných*.

### <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Tyto referenční proměnné vypadají podobně jako příkazy, které jste použili dříve pro přidání objektů (například `Timer` objektů, `List` objektů a `Random` objektů) do formuláře. Tyto příkazy však nezpůsobí, že se na formuláři zobrazí dva nadbytečné ovládací prvky Label, protože `new` v žádném z obou příkazů není použito žádné klíčové slovo. Bez `new` klíčového slova není objekt vytvořen. To je důvod, proč `firstClicked` a `secondClicked` jsou označovány jako referenční proměnné: pouze udržují sledování (nebo, odkaz na) `Label` objekty.

     Pokud proměnná neudržuje přehled o objektu, je nastavena na speciální rezervovanou hodnotu: `null` v jazyce Visual C# a `Nothing` v Visual Basic. Takže když se program spustí, i `firstClicked` `secondClicked` se nastaví na `null` nebo `Nothing` , což znamená, že proměnné neudržují přehled o cokoli.

2. Upravte obslužnou rutinu události Click tak, aby používala novou `firstClicked` referenční proměnnou. Odeberte poslední příkaz v `label_Click()` metodě obslužné rutiny události ( `clickedLabel.ForeColor = Color.Black;` ) a nahraďte ho `if` příkazem, který následuje. (Nezapomeňte přidat komentář a celý `if` příkaz.)

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program již sleduje první štítek, který hráč zvolí, takže se `firstClicked` nerovná `null` v jazyce Visual C# nebo `Nothing` v Visual Basic. Když `if` příkaz zkontroluje, `firstClicked` zda je roven `null` nebo `Nothing` , zjistí, že není a neprovede příkazy v `if` příkazu. Takže pouze první ikona, která je vybrána, zčerná a další ikony jsou skryté, jak je znázorněno na následujícím obrázku.

     ![Porovnávací hra ukazující jednu ikonu](../ide/media/express-tut4step5.png "Express_Tut4Step5") Porovnávací hra ukazující jednu ikonu

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího prvku **Timer** .

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek 6: Přidání časovače](../ide/step-6-add-a-timer.md).

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).
