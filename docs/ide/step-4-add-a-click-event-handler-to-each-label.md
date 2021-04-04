---
title: 'Krok 4: Přidání obslužné rutiny události Click ke každému popisku'
description: Přečtěte si, jak přidat obslužnou rutinu události Click do každého popisku.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931bd4191331f229f40a813b605eac7f69a1427a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214275"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidání obslužné rutiny události Click ke každému popisku

Porovnávací hra probíhá takto:

1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.

2. Potom hráč zvolí jinou skrytou ikonu.

3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.

   Chcete-li programu pracovat tímto způsobem, přidejte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události, která změní barvu vybraného popisku.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Přidání obslužné rutiny události Click do každého popisku

1. Otevřete formulář v **Návrhář formulářů**. V **Průzkumník řešení** vyberte *Form1. cs* nebo *Form1. vb*. Na panelu nabídek vyberte možnost Návrhář **zobrazení**  >  .

2. Vyberte první ovládací prvek popisku. Pak podržte stisknutou klávesu **CTRL** a vyberte všechny ostatní štítky, které chcete vybrat. Je nutné vybrat všechny popisky.

3. Kliknutím na tlačítko **události** na panelu nástrojů v okně **vlastnosti** zobrazte stránku **události** v okně **vlastnosti** . Posuňte se dolů k události **Click** a do pole zadejte **label_Click** , jak je znázorněno na následujícím snímku obrazovky.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_labelclick.png)

4. Klikněte na klávesu **ENTER** . Rozhraní IDE přidá `Click` obslužnou rutinu události volanou `label_Click()` kódu a připojí ji ke každému popisku ve formuláři.

5. Vyplňte zbývající část kódu takto:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet4":::

    > [!IMPORTANT]
    > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment kódu jazyka C# nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Pokud zkopírujete a vložíte `label_Click()` blok kódu místo ručního zadání kódu, nezapomeňte nahradit stávající `label_Click()` kód. Jinak budete mít duplicitní kód bloku.

    > [!NOTE]
    > Můžete rozpoznat `object sender` v horní části obslužné rutiny události, která se používá v [kurzu 2: vytvoření časovaného kurzu matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md) . Vzhledem k tomu, že jste se připojili k jedné metodě obslužné rutiny události, jste přivolali různé události ovládacího prvku popisek, je stejná metoda volána bez ohledu na to, která jmenovka uživatel zvolí. Metoda obslužné rutiny události musí znát, který popisek byl vybrán, takže používá název `sender` k identifikaci ovládacího prvku popisek. První řádek metody oznamuje programu, že to není pouze obecný objekt, ale konkrétně ovládací prvek popisku a který používá název `clickedLabel` pro přístup k vlastnostem a metodám popisku.

     Tato metoda nejprve ověří, zda `clickedLabel` byla úspěšně převedena (přetypování) z objektu na ovládací prvek popisku. V případě neúspěchu má hodnotu `null` (C#) nebo `Nothing` (Visual Basic) a nechcete spustit zbytek kódu v metodě. V dalším kroku metoda zkontroluje barvu textu zvolené jmenovky pomocí vlastnosti **ForeColor** popisku. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To je to, co `return` příkaz dělá: oznamuje programu, aby zastavil provádění metody.) V opačném případě se ikona nezvolila, takže program změní barvu textu popisku na černou.

6. Na panelu nabídek **Zvolte možnost**  >  **Uložit vše** a uložte průběh. potom v řádku nabídek zvolte **ladění**  >  **Spustit ladění** a program spusťte. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 3: přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md).
