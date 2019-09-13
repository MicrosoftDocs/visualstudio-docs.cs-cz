---
title: 'Krok 6: Pojmenování tlačítkových ovládacích prvků'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc843cceea35d196e3f9719a0690764611865600
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887976"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Pojmenování tlačítkových ovládacích prvků

Ve formuláři je pouze <xref:System.Windows.Forms.PictureBox> jeden. Po přidání se rozhraní IDE automaticky jmenuje **pictureBox1**. Existuje pouze jeden <xref:System.Windows.Forms.CheckBox>, který má název **checkBox1**. Brzy napíšete kód a tento kód bude odkazovat na zaškrtávací políčko a PictureBox. Vzhledem k tomu, že existuje pouze jeden z těchto ovládacích prvků, budete znát, co to znamená, když ve svém kódu uvidíte **pictureBox1** nebo **checkBox1** .

> [!TIP]
> V Visual Basic výchozí první písmeno libovolného názvu ovládacího prvku má počáteční zakončení, takže názvy jsou **pictureBox1**, **checkBox1**a tak dále.

Ve formuláři jsou čtyři tlačítka a rozhraní IDE s názvem **Button1**, **Button2**, **Button3**a **Button4**. Pouhým zobrazením jejich aktuálních názvů nevíte, které tlačítko představuje tlačítko **Zavřít** a který je jedním z tlačítek **Zobrazit obrázek** . To je důvod, proč vaše tlačítko ovládá více informativních názvů je užitečné.

## <a name="to-name-your-button-controls"></a>Chcete-li pojmenovat ovládací prvky tlačítka

1. Ve formuláři klikněte na tlačítko **Zavřít** . (Pokud máte stále vybraná všechna tlačítka, kliknutím na klávesu **ESC** výběr zrušte.) Posuňte se v okně **vlastnosti** , dokud se nezobrazí vlastnost **(název)** . (Vlastnost **(Name)** je blízko horní části, pokud jsou vlastnosti seřazené abecedně.) Změňte název na **closeButton**, jak je znázorněno na následujícím snímku obrazovky.

    ![okno Vlastnosti s názvem closeButton](../ide/media/express_setnameproperty.png)<br>***Vlastnosti*** *okno s* ***closeButton*** *název*

    > [!NOTE]
    > Zkuste změnit název tlačítka na **tlačítko Zavřít**s mezerou mezi slovy "Zavřít" a "tlačítko". Když to uděláte, rozhraní IDE zobrazí chybovou zprávu: Hodnota vlastnosti není platná. Mezery (a několik dalších znaků) nejsou povoleny v názvech ovládacích prvků.

1. Přejmenujte další tři tlačítka na **backgroundButton**, **clearButton**a **showButton**.
Názvy můžete ověřit tak, že v okně **vlastnosti** zvolíte rozevírací seznam výběr ovládacího prvku. Nové názvy tlačítek se zobrazí.

1. Dvakrát klikněte na tlačítko **Zobrazit obrázek** ve formuláři. Jako alternativu zvolte na formuláři tlačítko **Zobrazit obrázek** a potom stiskněte klávesu **ENTER** . Když to uděláte, IDE otevře další kartu v hlavním okně s názvem **Form1.cs**. (Pokud používáte Visual Basic, karta má název **Form1. vb**).

   Tato karta zobrazuje soubor kódu za formulářem, jak je znázorněno na následujícím snímku obrazovky.

    ![Karta Form1.cs s kódem Visual&#35; C](../ide/media/express_showbuttoncode.png)<br>
Karta ***Form1.cs*** *s C# kódem*

    > [!NOTE]
    > Karta Form1.cs může místo toho zobrazovat **showButton** jako **showButton** .

1. Zaměřte se na tuto část kódu.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click
    
    End Sub
    ```

   > [!IMPORTANT]
   > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

   Díváte jste se na kód s `showButton_Click()` názvem ( `ShowButton_Click()`případně). Rozhraní IDE bylo přidáno do kódu formuláře při otevření souboru kódu pro tlačítko **showButton** . V době návrhu při otevření souboru kódu pro ovládací prvek ve formuláři se kód vygeneruje pro ovládací prvek, pokud ještě neexistuje. Tento kód, který se označuje jako *Metoda*, se spouští při spuštění aplikace a výběru ovládacího prvku – v tomto případě se **zobrazí tlačítko Zobrazit obrázek** .

1. Zvolte znovu kartu **Návrhář formulářů** (**Form1.cs [Design]** ) a pak otevřete soubor kódu pro tlačítko **Vymazat obrázek** pro vytvoření metody v kódu formuláře. Tento postup opakujte pro zbývající dvě tlačítka. V každém okamžiku rozhraní IDE přidá novou metodu do souboru kódu formuláře.

1. Chcete-li přidat další metodu, otevřete soubor kódu pro ovládací prvek **CheckBox** v **Návrhář formulářů** , aby `checkBox1_CheckedChanged()` rozhraní IDE přidalo metodu. Tato metoda je volána vždy, když uživatel vybere nebo zruší zaškrtnutí políčka.

   > [!TIP]
   > Při práci na aplikaci se často přesouváte mezi editorem kódu a **Návrhář formulářů**. Rozhraní IDE usnadňuje navigaci v projektu. Pomocí **Průzkumník řešení** otevřít **Návrhář formulářů** dvojím kliknutím na *Form1.cs* v C# nebo *Form1. vb* v Visual Basic nebo na panelu nabídek vyberte možnost**Návrhář** **zobrazení** > .

    Následující příklad ukazuje nový kód, který se zobrazí v editoru kódu.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]
    
    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    Pět metod, které jste přidali, se nazývají *obslužné rutiny událostí*, protože vaše aplikace je volá vždy, když dojde k události (jako je například uživatel výběr tlačítka nebo výběru pole).

    Při zobrazení kódu pro ovládací prvek v rozhraní IDE v době návrhu, Visual Studio přidá metodu obslužné rutiny události pro ovládací prvek, pokud žádný není. Například když dvakrát kliknete na tlačítko, rozhraní IDE přidá obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost (která je volána vždy, když uživatel zvolí tlačítko). Když dvakrát kliknete na zaškrtávací políčko, rozhraní IDE přidá obslužnou rutinu události pro <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost (která je volána vždy, když uživatel vybere nebo zruší pole).

    Po přidání obslužné rutiny události pro ovládací prvek se k němu můžete kdykoli vrátit z **Návrhář formulářů** dvojitým kliknutím na ovládací prvek nebo na řádku nabídek, výběrem možnosti **Zobrazit** > **kód**.

    Názvy jsou důležité při sestavování programů a metody (včetně obslužných rutin událostí) můžou mít libovolný název, který chcete. Když přidáte obslužnou rutinu události s rozhraním IDE, vytvoří se název založený na názvu ovládacího prvku a události, která je zpracovávána.

    Například událost Click pro tlačítko s názvem **showButton** se nazývá `showButton_Click()` metoda obslužné rutiny události (případně `ShowButton_Click()`). Také se za názvem metody obvykle přidávají otevírací a uzavírací závorky `()` , které označují, že se metody diskutuje.

    Pokud se rozhodnete, že chcete změnit název proměnné kódu, klikněte pravým tlačítkem myši na proměnnou v kódu a pak zvolte příkaz **refaktor** > **Rename**. Všechny instance této proměnné v kódu jsou přejmenovány. Další informace najdete v tématu [refaktoringu přejmenování](../ide/reference/rename.md).

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si  **[článek krok 7: Přidejte součásti dialogového okna do formuláře](../ide/step-7-add-dialog-components-to-your-form.md).**

* Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 5: Přidejte ovládací prvky do formuláře](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Viz také:

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: Vytvořit porovnávací hru](tutorial-3-create-a-matching-game.md)
