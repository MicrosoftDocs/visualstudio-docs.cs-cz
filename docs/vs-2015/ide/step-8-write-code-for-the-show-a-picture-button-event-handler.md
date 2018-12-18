---
title: 'Krok 8: Zapište kód pro zobrazení obslužné rutiny události obrázku tlačítka | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6172188fb7d06122cdcc178889b2a5b37ca1bb0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933544"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Zapište kód pro obslužnou rutinu události zobrazení tlačítka s obrázkem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku provedete **zobrazit obrázek** tlačítko jako funkční následujícím způsobem:  
  
- Když uživatel vybere toto tlačítko, program otevře **otevřít soubor** dialogové okno.  
  
- Pokud uživatel otevře soubor s obrázkem, program zobrazí v ovládacím prvku PictureBox daný obrázek.  
  
  Rozhraní IDE má výkonný nástroj zvaný technologie IntelliSense, která vám pomůže psát kód. Při zadávání kódu, rozhraní IDE otevře pole s navrhovaným dokončením pro částečná slova, která zadáte. Pokusí se zjistit, co chcete udělat dále a automaticky přejde na poslední položku, kterou si vybrat ze seznamu. Můžete použít nahoru nebo dolů šipkami přesunout v seznamu, nebo můžete pokračovat v psaní písmen k zúžení voleb. Když se zobrazí možnosti, kterou chcete, zvolte klávesu TAB a vyberte ji. Nebo můžete návrhy ignorovat, pokud nejsou potřebné.  
  
  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 4](http://go.microsoft.com/fwlink/?LinkId=205215) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 4](http://go.microsoft.com/fwlink/?LinkId=205203). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Psaní kódu pro zobrazení obslužné rutiny události obrázku tlačítka  
  
1.  Přejděte do Návrháře formulářů Windows a dvakrát klikněte **zobrazit obrázek** tlačítko. Rozhraní IDE ihned přejde na návrháře kódu a přesune kurzor tak, aby byl uvnitř `showButton_Click()` metodu, která jste přidali dříve.  
  
2.  Typ `i` na prázdném řádku mezi těmito dvěma závorkami {}. (V jazyce Visual Basic zadejte na prázdném řádku mezi privátní podprogram... a End Sub.) **IntelliSense** otevře se okno, jak je znázorněno na následujícím obrázku.  
  
     ![Technologie IntelliSense s Visual C&#35; kód](../ide/media/express-ifintellisense.png "Express_IfIntellisense")  
Technologie IntelliSense s kódem Visual C#  
  
3.  **IntelliSense** okno by mělo zvýrazňovat slovo **Pokud**. (Pokud ne, zadejte malé `f`, a to bude.) Všimněte si, jak trochu *popisek* políčko vedle možnosti **IntelliSense** s popisem, zobrazí se okno **fragment kódu pro příkaz**. (V jazyce Visual Basic popis tlačítka také uvádí, že to je fragment kódu, ale s mírně odlišným zněním.) Chcete-li použít tento fragment, proto zvolte klávesu Tabulátor k vložení **Pokud** do kódu. Zvolte klávesu Tabulátor znovu pro použití **Pokud** fragment kódu. (Pokud jste zvolili jinam a **IntelliSense** okno zmizelo, smažte vše přes **můžu** a znovu jej napište a **IntelliSense** znovu otevře se okno.)  
  
     ![Visual C&#35; kód](../ide/media/express-highlighttrue.png "Express_HighlightTrue")  
Kód Visual C#  
  
4.  Pak pomocí technologie IntelliSense k zadání dalšího kódu k otevření **otevřít soubor** dialogové okno. Pokud uživatel vybral **OK** tlačítka, ovládací prvek PictureBox načte soubor, který uživatel vybral. Následující kroky ukazují, jak zadat kód, a přestože je to mnoho kroků, je pouze několik klávesových úhozů:  
  
    1.  Začněte s vybraným textem **true** v tomto fragmentu kódu. Typ `op` k jeho přepsání. (V jazyce Visual Basic začíná počátečním velkým, proto zadejte `Op`.)  
  
    2.  **IntelliSense** okno se otevře a zobrazí **openFileDialog1**. Zvolte klávesu TAB a vyberte ji. (V jazyce Visual Basic začíná počátečním velkým písmenem, takže se zobrazí **OpenFileDialog1**. Ujistěte se, že **OpenFileDialog1** je vybrán.)  
  
         Další informace o `OpenFileDialog`, naleznete v tématu [OpenFileDialog](http://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).  
  
    3.  Zadejte tečku (`.`) (mnoho programátorů to tečku.) Protože jste zadali tečku ihned po **openFileDialog1**, **IntelliSense** otevře se okno vyplněné se všemi **OpenFileDialog** vlastnostmi a metodami komponenty. Jedná se o stejné vlastnosti, které se zobrazují v **vlastnosti** okno při výběru v Návrháři formulářů Windows. Můžete také metody, které říct komponentě, aby provedla věci (jako je otevření dialogového okna).  
  
        > [!NOTE]
        >  **IntelliSense** můžete v okně zobrazí vlastnosti a metody. Pokud chcete zjistit, co je zobrazeno, podívejte se na ikonu na levé straně každé položky v **IntelliSense** okna. Vidíte obrázek bloku vedle každé metody a obrázek klíče (nebo spanner) vedle jednotlivých vlastností. Je zde také ikona blesku vedle každé události. Tyto obrázky se zobrazí takto.  
  
         ![Ikona metody](../ide/media/express-iconmethod.png "Express_IconMethod")  
Ikona metody  
  
         ![Ikona vlastnost](../ide/media/express-iconproperty.png "Express_IconProperty")  
Ikona vlastnost  
  
         ![Ikona události](../ide/media/express-iconevent.png "Express_IconEvent")  
Ikona události  
  
    4.  Začněte zadáním `ShowDialog` (malá a velká písmena nejsou důležitá pro technologii IntelliSense). `ShowDialog()` Metoda se zobrazí **otevřít soubor** dialogové okno. Poté, co okno zvýraznilo **ShowDialog**, stiskněte klávesu Tabulátor. Můžete také zvýraznit "ShowDialog" a stisknutím klávesy F1 pro něj zobrazit nápovědu.  
  
         Další informace o `ShowDialog()` metodu, najdete v článku [metody ShowDialog](http://msdn.microsoft.com/library/c7ykbedk.aspx).  
  
    5.  Při použití metody u ovládacího prvku nebo komponenty (označované jako *volání metody*), je třeba přidat závorky. Zadejte proto počáteční a ihned po "g" v `ShowDialog`: `()` by měl nyní vypadat takto: "openFileDialog1.ShowDialog()".  
  
        > [!NOTE]
        >  Metody jsou důležitou součástí každého programu a tento kurz ukázal několik způsobů, jak používat metody. Můžete volat metodu komponenty, které sděluje, má něco udělat, jako jste volali **OpenFileDialog** komponenty `ShowDialog()` metody. Můžete vytvořit vlastní metody, aby váš program prováděl akce, jako vytváříte nyní, volá se, `showButton_Click()` metodu, která otevře dialogové okno a obrázek, když uživatel vybere tlačítko.  
  
    6.  Pro jazyk Visual C# přidejte mezeru a pak přidejte dva symboly rovná se (`==`). V jazyce Visual Basic přidejte mezeru a pak používat jediný symbol rovnítka (`=`). (Visual C# a Visual Basic používá odlišné operátory rovnosti.)  
  
    7.  Přidejte další mezeru. Jakmile provedete, jiné **IntelliSense** otevře se okno. Začněte zadáním `DialogResult` a stiskněte klávesu TAB a přidejte ji.  
  
        > [!NOTE]
        >  Při psaní kódu pro volání metody, někdy vrací hodnotu. V takovém případě **OpenFileDialog** komponenty `ShowDialog()` metoda vrátí hodnotu DialogResult. DialogResult je zvláštní hodnota, která zjistíte, co se stalo v dialogovém okně. **OpenFileDialog** komponenta může vést k výběru uživatele **OK** nebo **zrušit**, takže jeho `ShowDialog()` metoda vrátí buď DialogResult.OK nebo DialogResult.Cancel.  
  
    8.  Zadejte tečku k otevření hodnotu DialogResult **IntelliSense** okna. Zadejte písmeno `O` a stiskněte klávesu TAB k vložení **OK**.  
  
         Další informace o `DialogResult`, naleznete v tématu [DialogResult](http://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).  
  
        > [!NOTE]
        >  První řádek kódu by měl být úplný. Pro jazyk Visual C# to mělo být jako následující.  
        >   
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`  
        >   
        >  V jazyce Visual Basic mělo být jako následující.  
        >   
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`  
  
    9. Nyní můžete přidáte další řádek kódu. Můžete ji zadat (nebo zkopírujte a vložte ji), ale zvažte použití technologie IntelliSense a přidejte ji. Více se seznámíte s podporou technologie IntelliSense, tím rychleji můžete napsat vlastní kód. Výsledná `showButton_Click()` metoda vypadá takto. (Zvolte **VB** kartu k zobrazení verze kódu jazyka Visual Basic.)  
  
         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 9: revize, komentáře a Test kódu](../ide/step-9-review-comment-and-test-your-code.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 7: komponenty dialogového okna Přidat na svůj formulář](../ide/step-7-add-dialog-components-to-your-form.md).



