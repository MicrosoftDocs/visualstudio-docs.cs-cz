---
title: 'Krok 5: Přidání odkazů na štítky'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de89d7194425e1a8cba9e11f2734372d80b256b3
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579325"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidání odkazů na štítky
Program potřebuje sledovat, která jmenovka řídí, aby hráč zvolil. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Váš program teď bude sledovat, který ovládací prvek popisek je vybraný jako první a který se volí za druhým pomocí *referenčních proměnných*.

## <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![programové řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Tyto referenční proměnné vypadají podobně jako příkazy, které jste použili dříve pro přidání objektů (například objektů <xref:System.Windows.Forms.Timer>, objektů <xref:System.Collections.Generic.List%601> a objektů <xref:System.Random>) do formuláře. Tyto příkazy však nezpůsobí, že se na formuláři zobrazí dva nadbytečné ovládací prvky Label, protože v jednom z obou příkazů není použito žádné `new` klíčové slovo. Bez klíčového slova `new` není vytvořen žádný objekt. To je důvod, proč `firstClicked` a `secondClicked` se nazývají referenční proměnné: pouze udržují přehled (nebo odkaz na) objekty popisků.

     Pokud proměnná neudržuje přehled o objektu, je nastavena na speciální rezervovanou hodnotu: `null` v C# a `Nothing` v Visual Basic. Takže když se program spustí, `firstClicked` i `secondClicked` jsou nastavené na `null` nebo `Nothing`, což znamená, že proměnné neudržují přehled o cokoli.

2. Upravte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> tak, aby používala novou referenční proměnnou `firstClicked`. Odeberte poslední příkaz v metodě obslužné rutiny události `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) a nahraďte ho příkazem `if`, který následuje. (Nezapomeňte přidat komentář a celý příkaz `if`.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program už sleduje první štítek, který hráč zvolí, takže `firstClicked` se ne`null` v C# Visual Basic nebo `Nothing`. Když váš příkaz `if` kontroluje `firstClicked` Chcete-li určit, zda se rovná `null` nebo `Nothing`, zjistí, že není a neprovede příkazy v příkazu `if`. Proto pouze první ikona, která je vybrána, se změní na černou a ostatní ikony jsou neviditelné, jak je znázorněno na následujícím obrázku.

     ![se porovnávací hra ukazující jednu ikonu](../ide/media/express_tut4step5.png)<br/>
***Porovnávací hra*** *ukazující jednu ikonu*

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího prvku **Timer** .

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek 6: Přidání časovače](../ide/step-6-add-a-timer.md)** .

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).
