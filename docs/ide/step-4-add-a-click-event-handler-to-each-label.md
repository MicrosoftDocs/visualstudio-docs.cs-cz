---
title: 'Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04054d353e0260e7a38a189fc6946aacd353b6c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897950"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí

Porovnávací hra probíhá takto:

1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.

2. Potom hráč zvolí jinou skrytou ikonu.

3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.

   Aby program takto fungoval, je přidat <xref:System.Windows.Forms.Control.Click> obslužná rutina události, která změní barvu vybraného popisku.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Přidat k jednotlivým jmenovkám obslužnou rutinu události kliknutí

1.  Otevřete formulář v nástrojích pro **Návrháře formulářů Windows**. V **Průzkumníka řešení**, zvolte *Form1.cs* nebo *Form1.vb*. V panelu nabídky zvolte **zobrazení** > **návrháře**.

2.  Vyberte první ovládací prvek popisku. Potom podržte klávesu **Ctrl** klávesu klikněte na každý další popisek, vyberte je. Je nutné vybrat všechny popisky.

3.  Zvolte **události** tlačítko na panelu nástrojů v **vlastnosti** okno zobrazení **události** stránku **vlastnosti** okna. Přejděte dolů k položce **klikněte na tlačítko** události a zadejte **výraz label_Click** v poli, jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_labelclick.png)

4.  Zvolte **Enter** klíč. Rozhraní IDE přidá `Click` volá obslužná rutina události `label_Click()` kódu a připojí ji k jednotlivým popiskům ve formuláři.

5.  Vyplňte zbývající část kódu takto:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

    > [!NOTE]
    > Pokud zkopírujete a vložíte `label_Click()` blok kódu, spíše než ručního zadání kódu, nezapomeňte nahradit stávající `label_Click()` kódu. Jinak budete mít duplicitní kód bloku.

    > [!NOTE]
    > Můžete rozpoznat `object sender` v horní části obslužné rutiny události jako stejný jako ten používané [kurz 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md) kurzu. Protože jste připojili jiný popisek ovládacího prvku klepněte na tlačítko události do metody obslužné rutiny jedna událost, volání stejné metody bez ohledu na to, který popisek uživatel vybere. Metoda obslužné rutiny události potřebuje vědět, který popisek byl vybrán, takže použije jméno `sender` k identifikaci ovládacího prvku popisku. První řádek metody dává pokyn programu, že není pouze obecný objekt, ale specificky ovládací prvek popisku a používá název `clickedLabel` pro přístup k vlastnostem a metodám popisku.

     Tato metoda nejprve zkontroluje, jestli `clickedLabel` byl úspěšně převeden (přetypován) z objektu do ovládacího prvku popisku. Pokud neúspěšný, má hodnotu `null` (C#) nebo `Nothing` (Visual Basic), a nechcete provést zbytek kódu v metodě. Dále metoda zkontroluje barvu textu vybraného popisku pomocí popisku **ForeColor** vlastnost. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To `return` provádí příkaz: říká programu, že má zastavit spouštění metody.) V opačném případě ikona nebyla vybrána, takže program změní barvu textu popisku na černou.

6.  V panelu nabídky zvolte **souboru** > **Uložit vše** rozdělanou práci uložit, a pak na panelu nabídek zvolte **ladění** > **Start Ladění** ke spuštění programu. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 5: Přidejte odkazy na jmenovky](../ide/step-5-add-label-references.md).

-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 3: přiřaďte jednotlivým jmenovkám náhodné ikony](../ide/step-3-assign-a-random-icon-to-each-label.md).
