---
title: 'Krok 8: Napsat kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek'
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e2a81aa5328167d049a6031015c1c569b2c5e0d
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118903"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Napsat kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek

V tomto kroku uděláte tlačítko **Zobrazit obrázek** následujícím způsobem:

- Když uživatel zvolí toto tlačítko, aplikace otevře <xref:System.Windows.Forms.OpenFileDialog> pole.

- Pokud uživatel otevře soubor s obrázkem, aplikace zobrazí tento obrázek v <xref:System.Windows.Forms.PictureBox>.

Rozhraní IDE má výkonný nástroj nazvaný IntelliSense, který vám pomůže psát kód. Při psaní kódu IDE otevře pole s navrhovanými dokončeními pro částečná slova, která zadáte.

Technologie IntelliSense se pokusí určit, co chcete udělat dále, a automaticky přejde na poslední položku, kterou zvolíte ze seznamu. Můžete použít šipky nahoru a dolů pro pohyb v seznamu nebo můžete nechat zadat písmena pro zúžení voleb. Po zobrazení požadované možnosti vyberte klávesu **TAB** a vyberte ji. Případně můžete návrhy ignorovat, pokud nejsou potřeba.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Zápis kódu pro obslužnou rutinu události zobrazit tlačítko obrázku

1. Přejděte na **Návrhář formulářů** a dvakrát klikněte na tlačítko **Zobrazit obrázek** . Rozhraní IDE okamžitě přejde do návrháře kódu a přesune kurzor tak, aby byl uvnitř `showButton_Click()` metody ( `ShowButton_Click()`případně), kterou jste přidali dříve.

1. Zadejte do prázdného řádku mezi dvě `{ }`složené závorky. `i` (V Visual Basic zadejte do prázdného řádku mezi `Private Sub...` a `End Sub`.) Otevře se okno **technologie IntelliSense** , jak je znázorněno na následujícím obrázku.

    ![IntelliSense s kódem jazyka&#35; Visual C](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Váš kód nemusí zobrazit obslužné rutiny událostí ve camelCase písmenech.

1. Okno **technologie IntelliSense** by mělo zvýraznit slovo `if`. (Pokud ne, zadejte malá a `f`velká písmena.) Všimněte si, jak se pole *ToolTip* vedle okna **IntelliSense** zobrazí s popisem, **fragmentem kódu pro příkaz if**. (V Visual Basic Popis také uvádí, že se jedná o fragment, ale s mírně odlišným použitím slov.) Chcete použít tento fragment kódu, proto vyberte klávesu **tabulátor** pro vložení `if` do kódu. Potom znovu stiskněte klávesu **TAB** , aby se `if` fragment používal. (Pokud jste si zvolili někam jinde a okno **IntelliSense** zmizelo, `i` je třeba ho znovu zadat a znovu se otevře okno **IntelliSense** .)

    ![Kód Visual&#35; C](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Použití IntelliSense k zadání dalšího kódu

Dále pomocí technologie IntelliSense zadáte další kód pro otevření dialogového okna **otevřít soubor** . Pokud uživatel zvolil tlačítko **OK** , ovládací prvek PictureBox načte soubor, který uživatel vybral. Následující kroky ukazují, jak zadat kód a i když existuje mnoho kroků, je to jen pár klávesových úhozů:

 1. Začněte s vybraným textem **true** ve fragmentu. Typ `op` k jeho přepsání. (V Visual Basic začínáte počátečním zakončením, takže zadejte `Op`.)

 1. Otevře se okno **IntelliSense** a zobrazí se dialog **OpenFileDialog1**. Zvolte klávesu **TAB** a vyberte ji. (V Visual Basic začíná počátečním zakončením, takže se zobrazí dialog **OpenFileDialog1**. Ujistěte se, že je vybraná možnost **OpenFileDialog1** .)

     Další informace o `OpenFileDialog`naleznete v tématu [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Zadejte tečku (`.`) (mnoho programátorů zavolá tuto tečku.) Vzhledem k tomu, že jste zadali tečku hned po programu **OpenFileDialog1**, otevře se okno **technologie IntelliSense** , které se vyplní všemi vlastnostmi a metodami komponenty **OpenFileDialog** . Jedná se o stejné vlastnosti, které se zobrazí v okně **vlastnosti** při výběru v **Návrhář formulářů**. Můžete také zvolit metody, které instruují komponentu k provádění akcí (například otevření dialogového okna).

    > [!NOTE]
    > Okno **technologie IntelliSense** může zobrazit jak vlastnosti, tak metody. Chcete-li zjistit, co se zobrazuje, podívejte se na ikonu na levé straně každé položky v okně **IntelliSense** . Vedle každé z nich se zobrazí obrázek bloku a vedle každé vlastnosti se zobrazí obrázek klíče (nebo Spanner). Vedle každé události je také Ikona blesku. <br><br>Tady jsou ikony, které se zobrazí:<br><br>![Ikona metody](../ide/media/express_iconmethod.png)<br>![Ikona vlastnosti](../ide/media/express_iconproperty.png)<br>![Ikona události](../ide/media/express_iconevent.png)

 1. Začátek psaní `ShowDialog` (velká a malá písmena neimportují IntelliSense). Metoda zobrazí dialogové okno **otevřít soubor.** `ShowDialog()` Po zvýraznění okna **ShowDialog**klikněte na klávesu **TAB** . Můžete také zvýraznit "ShowDialog" a vybrat klávesu **F1** pro získání pro pomoc.

    Další informace o `ShowDialog()` metodě naleznete v tématu [Metoda ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Při použití metody v ovládacím prvku nebo součásti (označované jako *volání metody*) je nutné přidat závorky. Proto zadejte levou a pravou závorku hned za "g" v `ShowDialog`: `()`Měl by nyní vypadat například "openFileDialog1. ShowDialog ()".

    > [!NOTE]
    > Metody jsou důležitou součástí jakékoli aplikace a tento kurz ukázal několik způsobů použití metod. Můžete zavolat metodu komponenty a sdělit jí, že má dělat něco, jako jste volali `ShowDialog()` metodu **OpenFileDialog** komponentu. Můžete vytvořit vlastní metody, aby vaše aplikace provedla věci, jako je ta, kterou právě sestavíte, `showButton_Click()` nazývaná metoda, která otevře dialogové okno a obrázek, když uživatel zvolí tlačítko.

 1. C#V případě přidejte mezeru a pak přidejte dva symboly rovná se (`==`). Pro Visual Basic přidejte mezeru a pak použijte jeden znak rovná se (`=`). (C# a Visual Basic použít jiné operátory rovnosti.)

 1. Přidejte další mezeru. Jakmile to uděláte, otevře se jiné okno **IntelliSense** . Začněte zadáním `DialogResult` a kliknutím na klávesu **tabulátor** ho přidejte.

    > [!NOTE]
    > Při psaní kódu pro volání metody, někdy vrátí hodnotu. V tomto případě <xref:System.Windows.Forms.CommonDialog.ShowDialog> metoda komponenty **OpenFileDialog** vrátí <xref:System.Windows.Forms.DialogResult> hodnotu. DialogResult je speciální hodnota, která oznamuje, co se stalo v dialogovém okně. Komponenta **OpenFileDialog** může mít za následek, že uživatel klikne na **tlačítko OK** nebo `ShowDialog()` **Zrušit**, takže `DialogResult.OK` jeho `DialogResult.Cancel`metoda vrátí buď nebo.

 1. Zadejte tečku pro otevření okna hodnoty DialogResult **technologie IntelliSense** . Zadejte písmeno `O` a kliknutím na klávesu **TAB** vložte **OK**.

    Další informace o DialogResult naleznete v tématu [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > První řádek kódu by měl být dokončen. C#V případě by měl být podobný následujícímu.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  V případě Visual Basic by měl být následující.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Nyní přidejte další řádek kódu. Můžete ho zadat (nebo ho zkopírovat a vložit), ale zvažte použití technologie IntelliSense k jejímu přidání. Lépe se seznámíte s technologií IntelliSense a rychleji můžete napsat vlastní kód. Poslední `showButton_Click()` metoda by měla vypadat podobně jako následující kód.

    > [!IMPORTANT]
    > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si  **[krok 9: Přečtěte si, pokomentujte a](../ide/step-9-review-comment-and-test-your-code.md)otestujte svůj kód**.

* Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 7: Přidejte součásti dialogového okna do formuláře](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Viz také:

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: Vytvořit porovnávací hru](tutorial-3-create-a-matching-game.md)
