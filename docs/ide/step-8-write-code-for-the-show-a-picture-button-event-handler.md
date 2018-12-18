---
title: 'Krok 8: Zapište kód pro zobrazení obslužné rutiny události obrázku tlačítka'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2c76a6eb760e55659c7da4df2a1a341426f0c6e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671804"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Zapište kód pro zobrazení obslužné rutiny události obrázku tlačítka

V tomto kroku provedete **zobrazit obrázek** tlačítko jako funkční následujícím způsobem:

- Když uživatel vybere toto tlačítko, program otevře <xref:System.Windows.Forms.OpenFileDialog> pole.

- Pokud uživatel otevře soubor s obrázkem, program zobrazí tento obrázek <xref:System.Windows.Forms.PictureBox>.

Rozhraní IDE má výkonný nástroj zvaný technologie IntelliSense, která vám pomůže psát kód. Při zadávání kódu, rozhraní IDE otevře pole s navrhovaným dokončením pro částečná slova, která zadáte. Pokusí se zjistit, co chcete udělat dále a automaticky přejde na poslední položku, kterou si vybrat ze seznamu. Můžete použít nahoru nebo dolů šipkami přesunout v seznamu, nebo můžete pokračovat v psaní písmen k zúžení voleb. Když se zobrazí možnost chcete, zvolte **kartu** stisknutím klávesy. Nebo můžete návrhy ignorovat, pokud nejsou potřebné.

![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 4](https://msdn.microsoft.com/vstudio/gg315355.aspx). Toto video používá starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Vytvoření kódu pro zobrazení obslužné rutiny události obrázku tlačítka

1.  Přejděte na **Návrháře formulářů Windows** a dvakrát klikněte **zobrazit obrázek** tlačítko. Rozhraní IDE ihned přejde na návrháře kódu a přesune kurzor tak, aby byl uvnitř `showButton_Click()` metodu, která jste přidali dříve.

2.  Typ `i` na prázdném řádku mezi dvěma závorkami `{ }`. (V jazyce Visual Basic zadejte na prázdném řádku mezi `Private Sub...` a `End Sub`.) **IntelliSense** otevře se okno, jak je znázorněno na následujícím obrázku.

     ![Technologie IntelliSense s Visual C&#35; kódu](../ide/media/express_ifintellisense.png)

3.  **IntelliSense** okno by mělo zvýrazňovat slovo `if`. (Pokud ne, zadejte malé `f`, a to bude.) Všimněte si, jak trochu *popisek* políčko vedle možnosti **IntelliSense** s popisem, zobrazí se okno **fragment kódu pro příkaz**. (V jazyce Visual Basic popis tlačítka také uvádí, že to je fragment kódu, ale s mírně odlišným zněním.) Chcete-li použít tento fragment, proto zvolte **kartu** klíče pro vložení `if` do kódu. Klikněte na tlačítko **kartu** klíč znovu pro použití `if` fragment kódu. (Pokud jste zvolili jinam a **IntelliSense** okno zmizelo, smažte vše přes `i` a znovu jej napište a **IntelliSense** znovu otevře se okno.)

     ![Visual C&#35; kódu](../ide/media/express_highlighttrue.png)

4.  Pak pomocí technologie IntelliSense k zadání dalšího kódu k otevření **otevřít soubor** dialogové okno. Pokud uživatel vybral **OK** tlačítka, ovládací prvek PictureBox načte soubor, který uživatel vybral. Následující kroky ukazují, jak zadat kód, a přestože je to mnoho kroků, je pouze několik klávesových úhozů:

    1.  Začněte s vybraným textem **true** v tomto fragmentu kódu. Typ `op` k jeho přepsání. (V jazyce Visual Basic začíná počátečním velkým, proto zadejte `Op`.)

    2.  **IntelliSense** okno se otevře a zobrazí **openFileDialog1**. Zvolte **kartu** stisknutím klávesy. (V jazyce Visual Basic začíná počátečním velkým písmenem, takže se zobrazí **OpenFileDialog1**. Ujistěte se, že **OpenFileDialog1** je vybrán.)

         Další informace o `OpenFileDialog`, naleznete v tématu [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

    3.  Zadejte tečku (`.`) (mnoho programátorů to tečku.) Protože jste zadali tečku ihned po **openFileDialog1**, **IntelliSense** otevře se okno vyplněné se všemi **OpenFileDialog** vlastnostmi a metodami komponenty. Jedná se o stejné vlastnosti, které se zobrazují v **vlastnosti** okno, když je vyberete v **Návrháře formulářů Windows**. Můžete také metody, které říct komponentě, aby provedla věci (jako je otevření dialogového okna).

        > [!NOTE]
        > **IntelliSense** můžete v okně zobrazí vlastnosti a metody. Pokud chcete zjistit, co je zobrazeno, podívejte se na ikonu na levé straně každé položky v **IntelliSense** okna. Vidíte obrázek bloku vedle každé metody a obrázek klíče (nebo spanner) vedle jednotlivých vlastností. Je zde také ikona blesku vedle každé události. Tyto obrázky se zobrazí takto.

         ![Ikona metody](../ide/media/express_iconmethod.png)

         ![Ikona vlastnost](../ide/media/express_iconproperty.png)

         ![Ikona události](../ide/media/express_iconevent.png)

    4.  Začněte zadáním `ShowDialog` (malá a velká písmena nejsou důležitá pro technologii IntelliSense). `ShowDialog()` Metoda se zobrazí **otevřít soubor** dialogové okno. Poté, co okno zvýraznilo **ShowDialog**, zvolte **kartu** klíč. Můžete také zvýraznit "ShowDialog" a zvolte **F1** klíč pro něj zobrazit nápovědu.

         Další informace o `ShowDialog()` metodu, najdete v článku [metody ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

    5.  Při použití metody u ovládacího prvku nebo komponenty (označované jako *volání metody*), je třeba přidat závorky. Zadejte proto počáteční a ihned po "g" v `ShowDialog`: `()` by měl nyní vypadat takto: "openFileDialog1.ShowDialog()".

        > [!NOTE]
        > Metody jsou důležitou součástí každého programu a tento kurz ukázal několik způsobů, jak používat metody. Můžete volat metodu komponenty, které sděluje, má něco udělat, jako jste volali **OpenFileDialog** komponenty `ShowDialog()` metody. Můžete vytvořit vlastní metody, aby váš program prováděl akce, jako vytváříte nyní, volá se, `showButton_Click()` metodu, která otevře dialogové okno a obrázek, když uživatel vybere tlačítko.

    6.  Pro jazyk Visual C# přidejte mezeru a pak přidejte dva symboly rovná se (`==`). V jazyce Visual Basic přidejte mezeru a pak používat jediný symbol rovnítka (`=`). (Visual C# a Visual Basic používá odlišné operátory rovnosti.)

    7.  Přidejte další mezeru. Jakmile provedete, jiné **IntelliSense** otevře se okno. Začněte zadáním `DialogResult` a zvolte **kartu** klíč a přidejte ji.

        > [!NOTE]
        > Při psaní kódu pro volání metody, někdy vrací hodnotu. V takovém případě **OpenFileDialog** komponenty <xref:System.Windows.Forms.CommonDialog.ShowDialog> metoda vrátí hodnotu <xref:System.Windows.Forms.DialogResult> hodnotu. DialogResult je zvláštní hodnota, která zjistíte, co se stalo v dialogovém okně. **OpenFileDialog** komponenta může vést k výběru uživatele **OK** nebo **zrušit**, takže jeho `ShowDialog()` metoda vrátí buď `DialogResult.OK` nebo `DialogResult.Cancel`.

    8.  Zadejte tečku k otevření hodnotu DialogResult **IntelliSense** okna. Zadejte písmeno `O` a zvolte **kartu** klíče pro vložení **OK**.

         Další informace o DialogResult najdete v tématu [DialogResult](<xref:System.Windows.Forms.DialogResult>).

        > [!NOTE]
        >  První řádek kódu by měl být úplný. Pro jazyk Visual C# to mělo být jako následující.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  V jazyce Visual Basic mělo být jako následující.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Nyní můžete přidáte další řádek kódu. Můžete ji zadat (nebo zkopírujte a vložte ji), ale zvažte použití technologie IntelliSense a přidejte ji. Více se seznámíte s podporou technologie IntelliSense, tím rychleji můžete napsat vlastní kód. Výsledná `showButton_Click()` metoda vypadá takto. (Zvolte **VB** kartu k zobrazení verze kódu jazyka Visual Basic.)

         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 9: revize, komentovat a testují vytvořený kód](../ide/step-9-review-comment-and-test-your-code.md).

-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 7: přidejte do svého formuláře komponenty dialogových oken](../ide/step-7-add-dialog-components-to-your-form.md).
