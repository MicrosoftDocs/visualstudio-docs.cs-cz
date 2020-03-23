---
title: 'Krok 5: Přidání odkazů na popisky'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579325"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidání odkazů na popisky
Program musí sledovat, který label ovládá hráč zvolí. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Program bude nyní sledovat, který ovládací prvek Label je vybrán jako první a který je vybrán jako druhý pomocí *referenčních proměnných*.

## <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Tyto referenční proměnné vypadají podobně jako příkazy, které <xref:System.Windows.Forms.Timer> jste <xref:System.Collections.Generic.List%601> použili <xref:System.Random> dříve k přidání objektů (například objektů, objektů a objektů) do formuláře. Tyto příkazy však nezpůsobí, že se ve formuláři zobrazí `new` dva další ovládací prvky Label, protože v žádném z těchto dvou příkazů není použito žádné klíčové slovo. Bez `new` klíčového slova není vytvořen žádný objekt. To je `firstClicked` důvod, proč a `secondClicked` jsou nazývány referenční proměnné: Oni jen sledovat (nebo, odkazovat na) Label objekty.

     Pokud proměnná není sledování objektu, je nastavena na zvláštní `null` vyhrazenou hodnotu: v jazyce C# a `Nothing` v jazyce Visual Basic. Takže při spuštění programu, `firstClicked` `secondClicked` a to `null` `Nothing`jak a jsou nastaveny na nebo , což znamená, že proměnné nejsou sledování nic.

2. Upravte <xref:System.Windows.Forms.Control.Click> obslužnou `firstClicked` rutinu události tak, aby používala novou referenční proměnnou. Odeberte poslední `label_Click()` příkaz v`clickedLabel.ForeColor = Color.Black;`metodě obslužné rutiny události ( ) a nahraďte jej za následujícím příkazem. `if` (Ujistěte se, že jste `if` zahrnuli komentář a celé prohlášení.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program je již sledování první štítek, který `firstClicked` hráč zvolil, `null` takže není `Nothing` rovna v jazyce C# nebo v jazyce Visual Basic. Když `if` váš `firstClicked` příkaz zkontroluje, zda `null` je `Nothing`rovno nebo , zjistí, že není, a neprovede příkazy v příkazu. `if` Takže pouze první vybraná ikona zčerná a ostatní ikony jsou neviditelné, jak je znázorněno na následujícím obrázku.

     ![Porovnávací hra zobrazující jednu ikonu](../ide/media/express_tut4step5.png)<br/>
***Odpovídající hra*** *zobrazující jednu ikonu*

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího **prvku Timer.**

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 4: Přidání obslužné rutiny události Click ke každému popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).
