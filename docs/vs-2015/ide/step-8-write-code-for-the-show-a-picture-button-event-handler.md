---
title: 'Krok 8: Zapište kód pro obslužnou rutinu události zobrazit tlačítko obrázku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aaa522efe5cb69dd9334a2cc3db7fc2846b1af7a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646901"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Zapište kód pro obslužnou rutinu události zobrazení tlačítka s obrázkem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku nastavíte tlačítko **Zobrazit obrázek** jako funkční:

- Když uživatel zvolí toto tlačítko, program otevře dialogové okno **otevřít soubor** .

- Pokud uživatel otevře soubor s obrázkem, program zobrazí tento obrázek v ovládacím prvku PictureBox.

  Rozhraní IDE má výkonný nástroj nazvaný IntelliSense, který vám pomůže psát kód. Při zadávání kódu IDE otevře pole s navrhovanými dokončeními pro částečná slova, která zadáte. Pokusí se určit, co chcete udělat dále, a automaticky přejde na poslední položku, kterou zvolíte ze seznamu. Můžete použít šipky nahoru a dolů pro pohyb v seznamu nebo můžete nechat zadat písmena pro zúžení voleb. Po zobrazení požadované možnosti vyberte klávesu TAB a vyberte ji. Případně můžete návrhy ignorovat, pokud nejsou potřeba.

  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-Video 4](http://go.microsoft.com/fwlink/?LinkId=205215) nebo v [kurzu 1: vytvoření prohlížeče obrázků ve C# formátu-Video 4](http://go.microsoft.com/fwlink/?LinkId=205203). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Zápis kódu pro obslužnou rutinu události zobrazit tlačítko obrázku

1. Přejděte na Návrhář formulářů a dvakrát klikněte na tlačítko **Zobrazit obrázek** . Rozhraní IDE okamžitě přejde do návrháře kódu a přesune kurzor tak, aby byl uvnitř metody `showButton_Click()`, kterou jste přidali dříve.

2. Zadejte `i` prázdného řádku mezi dvě složené závorky {}. (V Visual Basic zadejte na prázdném řádku mezi Private sub... a ukončit proceduru.) Otevře se okno **technologie IntelliSense** , jak je znázorněno na následujícím obrázku.

     ![IntelliSense s Visual C&#35; Code](../ide/media/express-ifintellisense.png "Express_IfIntellisense") IntelliSense s vizuálním kódem C#

3. Okno **technologie IntelliSense** by mělo zvýrazňovat slovo **if**. (Pokud ne, zadejte `f` s malými písmeny a pak.) Všimněte si, jak se *zobrazí malé pole s popisem* vedle okna **technologie IntelliSense** s popisem, **fragmentem kódu pro příkaz if**. (V Visual Basic Popis také uvádí, že se jedná o fragment, ale s mírně odlišným použitím slov.) Chcete použít tento fragment kódu, proto vyberte klávesu TAB **a vložte ji** do svého kódu. Potom znovu stiskněte klávesu TAB a použijte tak fragment **if** . (Pokud jste zvolili někde jinde a okno **IntelliSense** zmizelo, místo na **i** a znovu ho zapište a otevře se okno **IntelliSense** znovu.)

     ![&#35; ](../ide/media/express-highlighttrue.png "Express_HighlightTrue") Vizuální C# kód Visual c++ Code

4. Dále pomocí technologie IntelliSense zadáte další kód pro otevření dialogového okna **otevřít soubor** . Pokud uživatel zvolil tlačítko **OK** , ovládací prvek PictureBox načte soubor, který uživatel vybral. Následující kroky ukazují, jak zadat kód a i když se jedná o mnoho kroků, je to jen pár klávesových úhozů:

    1. Začněte s vybraným textem **true** ve fragmentu. Zadejte `op` k jeho přepsání. (V Visual Basic začínáte počátečním zakončením, takže zadejte `Op`.)

    2. Otevře se okno **IntelliSense** a zobrazí se dialog **OpenFileDialog1**. Zvolte klávesu TAB a vyberte ji. (V Visual Basic začíná počátečním zakončením, takže se zobrazí dialog **OpenFileDialog1**. Ujistěte se, že je vybraná možnost **OpenFileDialog1** .)

         Další informace o `OpenFileDialog` naleznete v části [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Zadejte tečku (`.`) (mnoho programátorů zavolá tuto tečku.) Vzhledem k tomu, že jste zadali tečku hned po programu **OpenFileDialog1**, otevře se okno **technologie IntelliSense** , které se vyplní všemi vlastnostmi a metodami komponenty **OpenFileDialog** . Jedná se o stejné vlastnosti, které se zobrazí v okně **vlastnosti** při výběru v Návrhář formulářů. Můžete také zvolit metody, které instruují komponentu k provádění akcí (například otevření dialogového okna).

        > [!NOTE]
        > Okno **technologie IntelliSense** může zobrazit jak vlastnosti, tak metody. Chcete-li zjistit, co se zobrazuje, podívejte se na ikonu na levé straně každé položky v okně **IntelliSense** . Zobrazí se obrázek bloku vedle každé metody a obrázek klíče (nebo Spanner) vedle každé vlastnosti. Vedle každé události je také Ikona blesku. Tyto obrázky se zobrazí takto.

         ![Ikona metody](../ide/media/express-iconmethod.png "Express_IconMethod") Ikona metody

         ![Ikona vlastnosti](../ide/media/express-iconproperty.png "Express_IconProperty") Ikona vlastnosti

         ![Ikona události](../ide/media/express-iconevent.png "Express_IconEvent") Ikona události

    4. Začněte psát `ShowDialog` (velká písmena se neimportují do technologie IntelliSense). Metoda `ShowDialog()` zobrazí dialogové okno **otevřít soubor** . Po zvýraznění okna **ShowDialog**klikněte na klávesu TAB. Můžete také zvýraznit "ShowDialog" a vybrat klávesu F1 pro získání pro pomoc.

         Další informace o metodě `ShowDialog()` naleznete v tématu [Metoda ShowDialog](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. Při použití metody v ovládacím prvku nebo součásti (označované jako *volání metody*) je nutné přidat závorky. Proto zadejte levou a pravou závorku hned za "g" v `ShowDialog`: `()` by teď měla vypadat jako "openFileDialog1. ShowDialog ()".

        > [!NOTE]
        > Metody jsou důležitou součástí jakéhokoli programu a tento kurz ukázal několik způsobů použití metod. Můžete zavolat metodu komponenty a sdělit jí, že má dělat něco, jako jste volali metodu `ShowDialog()` komponenty **OpenFileDialog** . Můžete vytvořit vlastní metody, které umožní programu provádět věci, jako je ten, který právě sestavíte, označovaný jako metoda `showButton_Click()`, která otevře dialogové okno a obrázek, když uživatel zvolí tlačítko.

    6. Pro vizuál C#přidejte mezeru a pak přidejte dva symboly rovná se (`==`). Pro Visual Basic přidejte mezeru a pak použijte jeden symbol rovná se (`=`). (Vizuál C# a Visual Basic používají jiné operátory rovnosti.)

    7. Přidejte další mezeru. Jakmile to uděláte, otevře se jiné okno **IntelliSense** . Začněte psát `DialogResult` a kliknutím na klávesu TAB ji přidejte.

        > [!NOTE]
        > Při psaní kódu pro volání metody, někdy vrátí hodnotu. V tomto případě metoda **OpenFileDialog** komponenty `ShowDialog()` vrací hodnotu DialogResult. DialogResult je speciální hodnota, která oznamuje, co se stalo v dialogovém okně. Komponenta **OpenFileDialog** může mít za následek, že uživatel klikne na **tlačítko OK** nebo **Zrušit**, takže jeho `ShowDialog()` metoda vrátí buď DialogResult. ok, nebo DialogResult. Cancel.

    8. Zadejte tečku pro otevření okna hodnoty DialogResult **technologie IntelliSense** . Zadejte písmeno `O` a vyberte klávesu Tabulátor pro vložení **OK**.

         Další informace o `DialogResult` najdete v tématu [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > První řádek kódu by měl být dokončen. V případě C#vizuálu by měl být následující.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  V případě Visual Basic by měl být následující.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Nyní přidejte další řádek kódu. Můžete ho zadat (nebo ho zkopírovat a vložit), ale zvažte použití technologie IntelliSense k jejímu přidání. Lépe se seznámíte s technologií IntelliSense a rychleji můžete napsat vlastní kód. Vaše finální `showButton_Click()` metoda vypadá následovně. (Chcete-li zobrazit Visual Basic verzi kódu, klikněte na kartu **VB** .)

         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 9: kontrola, komentář a testování kódu](../ide/step-9-review-comment-and-test-your-code.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek 7: Přidání součástí dialogového okna do formuláře](../ide/step-7-add-dialog-components-to-your-form.md).
