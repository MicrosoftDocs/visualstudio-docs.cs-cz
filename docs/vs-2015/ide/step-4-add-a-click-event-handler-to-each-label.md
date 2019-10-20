---
title: 'Krok 4: přidejte do každého popisku obslužnou rutinu události Click | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b78a1757586dfaf6087711eaf1ed6001155a3b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671807"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Porovnávací hra probíhá takto:

1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.

2. Potom hráč zvolí jinou skrytou ikonu.

3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.

   Aby program takto fungoval, přidejte obslužnou rutinu události Click, která změní barvu vybraného popisku.

### <a name="to-add-a-click-event-handler-to-each-label"></a>Přidání obslužné rutiny události Click ke každému popisku

1. Otevřete formulář v Návrháři formulářů Windows. V Průzkumníku řešení vyberte soubor Form1.cs nebo Form1.vb. Na řádku nabídek klikněte na položku **zobrazení**, **Návrhář**.

2. Vyberte první ovládací prvek popisku. Potom podržte klávesu Ctrl a postupně klikněte na každý další popisek, abyste je vybrali. Je nutné vybrat všechny popisky.

3. Kliknutím na tlačítko **události** na panelu nástrojů v okně **vlastnosti** zobrazte stránku **události** v okně **vlastnosti** . Posuňte se dolů k události **Click** a do pole zadejte **label_Click** , jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express-labelclick.png "Express_labelClick") okno Vlastnosti zobrazující událost Click

4. Poté stiskněte klávesu ENTER. Rozhraní IDE přidá obslužnou rutinu události Click nazvanou `label_Click()` do kódu a připojí ji ke každému popisku ve formuláři.

5. Vyplňte zbývající část kódu takto:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]

    > [!NOTE]
    > Pokud zkopírujete a vložíte blok kódu `label_Click()` místo ručního zadání kódu, nezapomeňte nahradit existující kód `label_Click()`. Jinak budete mít duplicitní kód bloku.

    > [!NOTE]
    > Můžete rozpoznat `object sender` v horní části obslužné rutiny události, která se používá v [kurzu 2: vytvoření časovaného kurzu matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md) . Protože jste připojili různé události Click ovládacího prvku popisku k jedné metodě obslužné rutiny události, volá se stejná metoda bez ohledu na to, který popisek uživatel zvolil. Metoda obslužné rutiny události musí znát, který popisek byl vybrán, takže použije jméno **odesílatele** k identifikaci ovládacího prvku popisek. První řádek metody oznamuje programu, že to není pouze obecný objekt, ale konkrétně ovládací prvek popisku a který používá název **clickedLabel** pro přístup k vlastnostem a metodám popisku.

     Tato metoda nejprve ověří, zda **clickedLabel** byl úspěšně převeden (přetypování) z objektu na ovládací prvek popisku. V případě neúspěchu má hodnotu `null` (C#) nebo `Nothing` (Visual Basic) a nechcete spustit zbytek kódu v metodě. V dalším kroku metoda zkontroluje barvu textu zvolené jmenovky pomocí vlastnosti **ForeColor** popisku. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To je to, co příkaz `return` dělá: oznamuje programu, že má zastavit provádění metody.) V opačném případě se ikona nezvolila, takže program změní barvu textu popisku na černou.

6. V panelu nabídek zvolte **soubor**, **Uložit vše** a uložte průběh a potom v řádku nabídek zvolte **ladit**, **Spustit ladění** a spusťte program. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek 5: Přidání odkazů na štítky](../ide/step-5-add-label-references.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 3: přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md).
