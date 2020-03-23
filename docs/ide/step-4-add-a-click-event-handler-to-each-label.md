---
title: 'Krok 4: Přidání obslužné rutiny události kliknutí ke každému popisku'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7049271dddb4e763bf5ecb3760358bdd63e38df5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579345"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidání obslužné rutiny události kliknutí ke každému popisku

Porovnávací hra probíhá takto:

1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.

2. Potom hráč zvolí jinou skrytou ikonu.

3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.

   Chcete-li, aby program fungoval tímto způsobem, přidejte obslužnou rutinu <xref:System.Windows.Forms.Control.Click> události, která změní barvu zvoleného popisku.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Přidání obslužné rutiny události kliknutí ke každému popisku

1. Otevřete formulář v **Návrháři formulářů systému Windows**. V **Průzkumníku řešení**zvolte *Form1.cs* nebo *Form1.vb*. Na řádku nabídek zvolte **Zobrazit** > **Návrhář**.

2. Vyberte první ovládací prvek popisku. Potom podržte stisknutou klávesu **Ctrl** a vyberte je, abyste vybrali jednotlivé popisky. Je nutné vybrat všechny popisky.

3. Zvolte tlačítko **Události** na panelu nástrojů v okně **Vlastnosti,** chcete-li zobrazit stránku **Události** v okně **Vlastnosti.** Posuňte se dolů na událost **Click** a zadejte **label_Click** do pole, jak je znázorněno na následujícím snímku obrazovky.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_labelclick.png)

4. Zvolte **enter** klíč. IDE přidá `Click` obslužnou rutinu události volanou `label_Click()` do kódu a zavěsí ji ke každému popisku ve formuláři.

5. Vyplňte zbývající část kódu takto:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Pokud zkopírujete a vložíte blok `label_Click()` kódu, nikoli ručně, `label_Click()` nezapomeňte nahradit existující kód. Jinak budete mít duplicitní kód bloku.

    > [!NOTE]
    > Můžete rozpoznat `object sender` v horní části obslužné rutiny události jako stejný jako ten, který je použit v [kurzu 2: Vytvořit kurz testu matematiky načasovaný.](../ide/tutorial-2-create-a-timed-math-quiz.md) Vzhledem k tomu, že jste připojili různé události kliknutí ovládacího prvku popisku k metodě obslužné rutiny jedné události, je volána stejná metoda bez ohledu na to, který popisek uživatel zvolí. Metoda obslužné rutiny události musí vědět, `sender` který popisek byl vybrán, takže používá název k identifikaci ovládacího prvku popisku. První řádek metody říká programu, že se nejedná pouze o obecný objekt, ale konkrétně `clickedLabel` o ovládací prvek popisku a že používá název pro přístup k vlastnostem a metodám popisku.

     Tato metoda nejprve zkontroluje, zda `clickedLabel` byl úspěšně převeden (přetypování) z objektu na ovládací prvek popisek. Pokud neúspěšné, má hodnotu `null` (C#) nebo `Nothing` (Visual Basic) a nechcete spustit zbytek kódu v metodě. Dále metoda zkontroluje barvu textu vybraného popisku pomocí **vlastnosti ForeColor** popisku. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To je to, co `return` prohlášení dělá: Říká program zastavit provádění metody.) V opačném případě nebyla ikona vybrána, takže program změní barvu textu popisku na černou.

6. Na řádku nabídek zvolte **Uložit** > **vše** soubor, chcete-li svůj postup uložit, a potom na řádku nabídek zvolte **Ladění** > **spouštění ladění** a spusťte program. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 5: Přidání odkazů na popisky](../ide/step-5-add-label-references.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si postup 3: Přiřazení náhodné ikony ke každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md).
