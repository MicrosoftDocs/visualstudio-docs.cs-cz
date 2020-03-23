---
title: 'Krok 8: Napište kód pro obslužnou rutinu události tlačítka obrázku'
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579803"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Napište kód pro obslužnou rutinu události tlačítka obrázku

V tomto kroku provedete funkci **Zobrazit obrázek** takto:

- Když uživatel zvolí toto tlačítko, <xref:System.Windows.Forms.OpenFileDialog> aplikace otevře pole.

- Pokud uživatel otevře soubor s obrázkem, aplikace <xref:System.Windows.Forms.PictureBox>tento obrázek zobrazí v aplikaci .

IDE má výkonný nástroj s názvem IntelliSense, který vám pomůže psát kód. Při psaní kódu otevře ide okno s navrhovaným dokončením pro částečná slova, která zadáte.

Technologie IntelliSense se pokusí určit, co chcete dělat dál, a automaticky přejde na poslední položku, kterou vyberete ze seznamu. Pomocí šipek nahoru nebo dolů můžete v seznamu přesunout, nebo můžete pokračovat v psaní písmen a zúžit výběr. Až se zobrazí požadovaná volba, vyberte ji klávesou **Tabulátor.** Nebo můžete ignorovat návrhy, pokud nejsou potřeba.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Psaní kódu pro obslužnou rutinu události tlačítka obrázku

1. Přejděte do **Návrháře formulářů windows** a poklepejte na tlačítko **Zobrazit obrázek.** IDE okamžitě přejde do návrháře kódu a přesune `showButton_Click()` kurzor tak, aby byl uvnitř (alternativně) metoda, `ShowButton_Click()`která byla přidána dříve.

1. Zadejte `i` a na prázdné matné čáře mezi dvěma závorkami `{ }`. (V jazyce Visual Basic zadejte na prázdnou čáru mezi `Private Sub...` a `End Sub`.) Otevře se okno **IntelliSense,** jak je znázorněno na následujícím obrázku.

    ![Technologie IntelliSense s&#35; kódem Visual C](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Váš kód nemusí zobrazovat obslužné rutiny událostí v "camelCase" písmena.

1. Okno **IntelliSense** by mělo `if`zvýraznit slovo . (Pokud ne, zadejte `f`malá písmena a bude.) Všimněte si, jak se vedle okna **Technologie IntelliSense** zobrazí pole *s* popisem **Fragment kódu pro příkaz if**. (V jazyce Visual Basic popisek také uvádí, že se jedná o úryvek, ale s mírně odlišným zněním.) Chcete použít tento úryvek, proto zvolte `if` klávesu **Tab,** kterou chcete vložit do kódu. Pak znovu zvolte klávesu `if` **Tab,** abyste použili úryvek. (Pokud jste zvolili někde jinde a vaše okno **IntelliSense** zmizelo, backspace přes `i` a znovu zadejte a okno **IntelliSense** se znovu otevře.)

    ![Kód&#35; Visual C](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Použití technologie IntelliSense k zadání dalšího kódu

Dále pomocí technologie IntelliSense zadejte další kód pro otevření dialogového okna **Otevřít soubor.** Pokud uživatel zvolil tlačítko **OK,** PictureBox načte soubor, který uživatel vybral. Následující kroky ukazují, jak zadat kód, a přestože existuje mnoho kroků, je to jen několik úhozů:

 1. Začněte s vybraným textem **true** ve fragmentu. Zadejte, `op` chcete-li jej přepsat. (V jazyce Visual Basic začnete počátečním zakončením, proto zadejte `Op`.)

 1. Otevře se okno **IntelliSense** a zobrazí **se openFileDialog1**. Vyberte klávesu **Tabulátor.** (V jazyce Visual Basic začíná počáteční mačká, takže se zobrazí **OpenFileDialog1**. Ujistěte se, že je vybrána možnost **OpenFileDialog1.)**

     Další informace `OpenFileDialog`naleznete v [tématu OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Zadejte tečku (`.`) (Mnoho programátorů to nazývá tečkou.) Vzhledem k tomu, že jste zadali tečku hned po **otevřeníFileDialog1**, otevře se okno **IntelliSense,** které se vyplní všemi vlastnostmi a metodami komponenty **OpenFileDialog.** Jedná se o stejné vlastnosti, které se zobrazí v okně **Vlastnosti,** když ji vyberete v **Návrháři formulářů systému Windows**. Můžete také zvolit metody, které říkají komponentě, aby dělala věci (například otevření dialogového okna).

    > [!NOTE]
    > Okno **IntelliSense** vám může zobrazit vlastnosti i metody. Chcete-li zjistit, co se zobrazuje, podívejte se na ikonu na levé straně každé položky v okně **IntelliSense.** Vedle každé metody se zobrazí obrázek bloku a vedle každé vlastnosti obrázek klíče (nebo klíče). Vedle každé události je také ikona blesku. <br><br>Zde jsou ikony, které se objevují:<br><br>![Ikona metody](../ide/media/express_iconmethod.png)<br>![Ikona vlastnosti](../ide/media/express_iconproperty.png)<br>![Ikona události](../ide/media/express_iconevent.png)

 1. Začněte `ShowDialog` psát (velká písmena nejsou pro technologie IntelliSense důležitá). Metoda `ShowDialog()` zobrazí dialogové okno **Otevřít soubor.** Po zobrazení okna **zobrazitdialog**zvolte klávesu **Tabulátor.** Můžete také zvýraznit "ShowDialog" a zvolte klávesu **F1,** abyste získali pomoc.

    Další informace o `ShowDialog()` metodě naleznete v tématu [ShowDialog Method](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Při použití metody na ovládací prvek nebo součásti (označované jako *volání metody*), je třeba přidat závorky. Takže zadejte otevírací a uzavírací závorky `ShowDialog` `()` bezprostředně po "g" v : Nyní by měl vypadat jako "openFileDialog1.ShowDialog()".

    > [!NOTE]
    > Metody jsou důležitou součástí každé aplikace a tento kurz ukázal několik způsobů použití metod. Můžete volat metodu komponenty, aby jí řekli, aby něco udělala, `ShowDialog()` například jak jste nazvali metodu komponenty **OpenFileDialog.** Můžete si vytvořit vlastní metody, aby vaše aplikace dělat věci, jako `showButton_Click()` je ten, který vytváříte nyní, volal metoda, která otevře dialogové okno a obrázek, když uživatel vybere tlačítko.

 1. Pro C#přidejte mezeru a pak přidejte dva rovnítka (`==`). V jazyce Visual Basic přidejte mezeru a`=`potom použijte jeden znaménko rovná se ( ). (C# a Visual Basic používají různé operátory rovnosti.)

 1. Přidejte další mezeru. Jakmile tak učiníte, otevře se další okno **Technologie IntelliSense.** Začněte `DialogResult` psát a zvolte klávesu **Tab,** kterou chcete přidat.

    > [!NOTE]
    > Při psaní kódu pro volání metody někdy vrátí hodnotu. V tomto případě <xref:System.Windows.Forms.CommonDialog.ShowDialog> metoda komponenty **OpenFileDialog** vrátí hodnotu. <xref:System.Windows.Forms.DialogResult> DialogResult je speciální hodnota, která vám řekne, co se stalo v dialogovém okně. Komponenta **OpenFileDialog** může způsobit, že uživatel zvolí **OK** `DialogResult.OK` nebo `DialogResult.Cancel` **Cancel**, takže její `ShowDialog()` metoda vrátí buď nebo .

 1. Zadáním tečky otevřete okno **IntelliSense** s hodnotou DialogVýsledek. Zadejte `O` písmeno a zvolte klávesu **Tab** pro vložení **OK**.

    Další informace o DialoguResult, naleznete v [tématu DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > První řádek kódu by měl být úplný. Pro C# by měla být podobná následující.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Pro visual basic by mělo být následující.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Nyní přidejte ještě jeden řádek kódu. Můžete jej zadat (nebo zkopírovat a vložit), ale zvažte použití technologie IntelliSense a přidejte ji. Čím více jste obeznámeni s IntelliSense, tím rychleji můžete napsat svůj vlastní kód. Konečná `showButton_Click()` metoda by měla vypadat podobně jako následující kód.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít k dalšímu kroku kurzu, **[přečtěte si krok 9: Kontrola, komentování a testování kódu](../ide/step-9-review-comment-and-test-your-code.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si obrázek 7: Přidání součástí dialogového okna do formuláře](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
