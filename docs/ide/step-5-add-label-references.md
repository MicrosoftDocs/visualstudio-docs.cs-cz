---
title: 'Krok 5: Přidání odkazů popisků'
description: Naučte se, jak do formuláře přidat odkazy na popisky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 393f71c3360371122e86dc078aaa97c6963db325
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296271"
---
# <a name="step-5-add-label-references"></a>Krok 5: Přidání odkazů popisků
Program potřebuje sledovat, která jmenovka řídí, aby hráč zvolil. Nyní program zobrazí všechny popisky, které hráč zvolí. Ale to změníme. Po výběru prvního popisku by program měl zobrazit ikonu popisku. Po výběru druhého popisku by program měl krátce zobrazit obě ikony a pak je opět skrýt. Váš program teď bude sledovat, který ovládací prvek popisek je vybraný jako první a který se volí za druhým pomocí *referenčních proměnných*.

## <a name="to-add-label-references"></a>Přidání odkazů popisků

1. Pomocí následujícího kódu přidejte do formuláře odkazy popisku.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment kódu jazyka C# nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Tyto referenční proměnné vypadají podobně jako příkazy, které jste použili dříve pro přidání objektů (například <xref:System.Windows.Forms.Timer> objektů, <xref:System.Collections.Generic.List%601> objektů a <xref:System.Random> objektů) do formuláře. Tyto příkazy však nezpůsobí, že se na formuláři zobrazí dva nadbytečné ovládací prvky Label, protože `new` v žádném z obou příkazů není použito žádné klíčové slovo. Bez `new` klíčového slova není objekt vytvořen. To je důvod, proč `firstClicked` a `secondClicked` jsou označovány jako referenční proměnné: pouze udržují přehled o objektech popisků (nebo odkazují na ně).

     Pokud proměnná neudržuje přehled o objektu, je nastavena na speciální rezervovanou hodnotu: `null` v jazyce C# a `Nothing` v Visual Basic. Takže když se program spustí, i `firstClicked` `secondClicked` se nastaví na `null` nebo `Nothing` , což znamená, že proměnné neudržují přehled o cokoli.

2. Upravte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události tak, aby používala novou `firstClicked` referenční proměnnou. Odeberte poslední příkaz v `label_Click()` metodě obslužné rutiny události ( `clickedLabel.ForeColor = Color.Black;` ) a nahraďte ho `if` příkazem, který následuje. (Nezapomeňte přidat komentář a celý `if` příkaz.)

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Uložte program a spusťte jej. Vyberte jeden z ovládacích prvků popisku a zobrazí se jeho ikona.

4. Vyberte další ovládací prvek popisku a všimněte si, že se nic nestane. Program již sleduje první štítek, který hráč zvolí, takže se `firstClicked` nerovná `null` v jazyce C# nebo `Nothing` v Visual Basic. Když `if` příkaz zkontroluje, `firstClicked` zda je roven `null` nebo `Nothing` , zjistí, že není a neprovede příkazy v `if` příkazu. Proto pouze první ikona, která je vybrána, se změní na černou a ostatní ikony jsou neviditelné, jak je znázorněno na následujícím obrázku.

     ![Porovnávací hra zobrazující jednu ikonu](../ide/media/express_tut4step5.png)<br/>
***Porovnávací hra** _ _showing jednu ikonu *

     Tuto situaci opravíte v dalším kroku kurzu přidáním ovládacího prvku **Timer** .

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek 6: Přidání časovače](../ide/step-6-add-a-timer.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).
