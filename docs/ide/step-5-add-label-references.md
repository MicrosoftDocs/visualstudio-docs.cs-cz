---
title: 'Krok 5: Přidání odkazů popisků'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4580fb2a4c77949825b4e84a7aed7553ceffd981
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079407"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidání odkazů popisků
Program potřebuje sledovat, která jmenovka řídí, aby hráč zvolil. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Váš program teď bude sledovat, který ovládací prvek popisek je vybraný jako první a který se volí za druhým pomocí *referenčních proměnných*.

## <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Tyto referenční proměnné vypadají podobně jako příkazy, které jste použili dříve pro přidání objektů ( <xref:System.Windows.Forms.Timer> například objektů <xref:System.Collections.Generic.List%601> , objektů a <xref:System.Random> objektů) do formuláře. Tyto příkazy však nezpůsobí, že se na formuláři zobrazí dva nadbytečné ovládací prvky Label, protože `new` v žádném z obou příkazů není použito žádné klíčové slovo. `new` Bez klíčového slova není objekt vytvořen. To je důvod `firstClicked` , `secondClicked` proč a se nazývají referenční proměnné: Pouze udržují objekty popisků (nebo odkazují na ně).

     Pokud proměnná neudržuje přehled o objektu, je nastavena na speciální rezervovanou hodnotu: `null` v jazyce Visual C# a `Nothing` v Visual Basic. Takže když se `firstClicked` program spustí, i `secondClicked` se nastaví na `null` nebo `Nothing`, což znamená, že proměnné neudržují přehled o cokoli.

2. Upravte obslužnou rutinu `firstClicked` událostitak,abypoužívala<xref:System.Windows.Forms.Control.Click> novou referenční proměnnou. Odeberte poslední příkaz v `label_Click()` metodě obslužné rutiny události (`clickedLabel.ForeColor = Color.Black;`) `if` a nahraďte ho příkazem, který následuje. (Nezapomeňte přidat komentář a celý `if` příkaz.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program už sleduje první štítek, který hráč zvolí, `firstClicked` takže se `null` nerovná vizuálně C# nebo `Nothing` v Visual Basic. `firstClicked` `Nothing`Když příkaz zkontroluje, `if` zda je roven nebo,zjistí,ženeníaneprovedepříkazyvpříkazu.`null` `if` Takže pouze první ikona, která je vybrána, zčerná a další ikony jsou skryté, jak je znázorněno na následujícím obrázku.

     ![Porovnávací hra ukazující jednu](../ide/media/express_tut4step5.png)
ikonu, která**odpovídá hře** ukazující jednu ikonu

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího prvku **Timer** .

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [krok 6: Přidejte časovač](../ide/step-6-add-a-timer.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 4: Přidejte obslužnou rutinu události Click pro každý](../ide/step-4-add-a-click-event-handler-to-each-label.md)popisek.
