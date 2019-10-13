---
title: 'Krok 5: Přidání odkazů popisků'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fdcecbdac0a866bd5c6a15a78d8c0ba2a33051a
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289677"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidání odkazů popisků
Program potřebuje sledovat, která jmenovka řídí, aby hráč zvolil. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Váš program teď bude sledovat, který ovládací prvek popisek je vybraný jako první a který se volí za druhým pomocí *referenčních proměnných*.

## <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>@no__t – ovládací prvek jazyka pro Docs. Microsoft. com @ no__t-1

     Tyto referenční proměnné vypadají podobně jako příkazy, které jste použili dříve k přidání objektů (například objektů <xref:System.Windows.Forms.Timer>, objektů <xref:System.Collections.Generic.List%601> a objektů <xref:System.Random>) do formuláře. Tyto příkazy však nezpůsobí, že se na formuláři zobrazí dva nadbytečné ovládací prvky Label, protože žádné klíčové slovo `new` použité v obou příkazech. Bez klíčového slova `new` není vytvořen žádný objekt. To je důvod, proč `firstClicked` a `secondClicked` se nazývají referenční proměnné: Pouze udržují objekty popisků (nebo odkazují na ně).

     Pokud proměnná neudržuje přehled o objektu, je nastavena na speciální rezervovanou hodnotu: `null` v vizuálu C# a `Nothing` v Visual Basic. Takže když se program spustí, `firstClicked` i `secondClicked` jsou nastavené na `null` nebo `Nothing`, což znamená, že proměnné neudržují přehled o cokoli.

2. Upravte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> tak, aby používala novou referenční proměnnou `firstClicked`. Odeberte poslední příkaz v metodě obslužné rutiny události `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) a nahraďte ho následujícím příkazem `if`. (Nezapomeňte přidat komentář a celý příkaz `if`.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program už sleduje první štítek, který hráč zvolí, takže `firstClicked` se nerovná `null` v vizuálu C# nebo `Nothing` v Visual Basic. Když váš příkaz `if` zkontroluje `firstClicked` a určí, jestli se rovná `null` nebo `Nothing`, zjistí, že není, a neprovede příkazy v příkazu `if`. Takže pouze první ikona, která je vybrána, zčerná a další ikony jsou skryté, jak je znázorněno na následujícím obrázku.

     @no__t – hra 0Matching ukazující jednu ikonu @ no__t-1<br/>
**Porovnávací hra** ukazující jednu ikonu

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího prvku **Timer** .

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si @no__t 0Step 6: Přidejte časovač @ no__t-0.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si téma [Step 4: Přidejte obslužnou rutinu události Click pro každý popisek @ no__t-0.
