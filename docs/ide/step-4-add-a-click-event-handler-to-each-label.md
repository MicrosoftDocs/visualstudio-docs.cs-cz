---
title: 'Krok 4: Přidání obslužné rutiny události Click ke každému popisku'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0e60d71631b42636223c97666f006728a198434
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079369"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidání obslužné rutiny události Click ke každému popisku

Porovnávací hra probíhá takto:

1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.

2. Potom hráč zvolí jinou skrytou ikonu.

3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.

   Chcete-li programu pracovat tímto způsobem, přidejte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události, která změní barvu vybraného popisku.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Přidání obslužné rutiny události Click do každého popisku

1. Otevřete formulář v **Návrhář formulářů**. V **Průzkumník řešení**vyberte *Form1.cs* nebo *Form1. vb*. Na panelu nabídek vyberte možnost**Návrhář** **zobrazení** > .

2. Vyberte první ovládací prvek popisku. Pak podržte stisknutou klávesu **CTRL** a vyberte všechny ostatní štítky, které chcete vybrat. Je nutné vybrat všechny popisky.

3. Kliknutím na tlačítko **události** na panelu nástrojů v okně **vlastnosti** zobrazte stránku **události** v okně **vlastnosti** . Posuňte se dolů k události **Click** a do pole zadejte **label_Click** , jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_labelclick.png)

4. Klikněte na klávesu **ENTER** . Rozhraní IDE přidá `Click` obslužnou rutinu události `label_Click()` volanou kódu a připojí ji ke každému popisku ve formuláři.

5. Vyplňte zbývající část kódu takto:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

    > [!NOTE]
    > Pokud zkopírujete a vložíte `label_Click()` blok kódu místo ručního zadání kódu, nezapomeňte nahradit stávající `label_Click()` kód. Jinak budete mít duplicitní kód bloku.

    > [!NOTE]
    > Můžete rozpoznat `object sender` v horní části obslužné rutiny události, která se používá [v kurzu 2: Vytvoření časovaného kurzu matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md) Vzhledem k tomu, že jste se připojili k jedné metodě obslužné rutiny události, jste přivolali různé události ovládacího prvku popisek, je stejná metoda volána bez ohledu na to, která jmenovka uživatel zvolí. Metoda obslužné rutiny události musí znát, který popisek byl vybrán, takže používá název `sender` k identifikaci ovládacího prvku popisek. První řádek metody oznamuje programu, že to není pouze obecný objekt, ale konkrétně ovládací prvek popisku a který používá název `clickedLabel` pro přístup k vlastnostem a metodám popisku.

     Tato metoda nejprve ověří, `clickedLabel` zda byla úspěšně převedena (přetypování) z objektu na ovládací prvek popisku. V případě neúspěchu má hodnotu `null` (C#) nebo `Nothing` (Visual Basic) a nechcete spustit zbytek kódu v metodě. V dalším kroku metoda zkontroluje barvu textu zvolené jmenovky pomocí vlastnosti **ForeColor** popisku. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To je to, `return` co příkaz dělá: Oznamuje programu, že má zastavit provádění metody.) V opačném případě ikona nebyla vybrána, takže program změní barvu textu popisku na černou.

6. Na panelu nabídek zvolte možnost > **Uložit vše** **a uložte průběh**. potom v řádku nabídek zvolte **ladění** > **Spustit ladění** a program spusťte. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [krok 5: Přidejte odkazy](../ide/step-5-add-label-references.md)Label.

- Pokud se chcete vrátit k předchozímu kroku kurzu [, podívejte se na krok 3: Přiřaďte každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md)náhodnou ikonu.
