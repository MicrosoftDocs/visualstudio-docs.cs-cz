---
title: 'Krok 6: Pojmenování ovládacích prvků tlačítek'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579792"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Pojmenování ovládacích prvků tlačítek

Ve vašem formuláři je jen jeden. <xref:System.Windows.Forms.PictureBox> Když jste ji přidali, ide automaticky pojmenoval **pictureBox1**. Existuje pouze jeden <xref:System.Windows.Forms.CheckBox>, který se nazývá **checkBox1**. Brzy napíšete nějaký kód a tento kód bude odkazovat na CheckBox a PictureBox. Vzhledem k tomu, že existuje pouze jeden z těchto ovládacích prvků, budete vědět, co to znamená, když se zobrazí **pictureBox1** nebo **checkBox1** ve vašem kódu.

> [!TIP]
> V jazyce Visual Basic je výchozím prvním písmenem libovolného názvu ovládacího prvku počáteční zakončení, takže názvy jsou **PictureBox1**, **CheckBox1**a tak dále.

Ve formuláři jsou čtyři tlačítka a ide s názvem them **button1**, **button2**, **button3**a **button4**. Pouhým pohledem na jejich aktuální jména nevíte, které tlačítko je tlačítko **Zavřít** a které z nich je tlačítko **Zobrazit obrázek.** To je důvod, proč dává tlačítko ovládací prvky více informativní názvy je užitečné.

## <a name="to-name-your-button-controls"></a>Pojmenování ovládacích prvků tlačítek

1. Ve formuláři zvolte tlačítko **Zavřít.** (Pokud máte stále vybraná všechna tlačítka, zvolte klávesu **Esc,** chcete-li výběr zrušit.) Posuňte se v okně **Vlastnosti,** dokud se nezobrazí vlastnost **(Název).** (Vlastnost **(Název)** je v horní části, pokud jsou vlastnosti abecední.) Změňte název na **closeButton**, jak je znázorněno na následujícím snímku obrazovky.

    ![Okno Vlastnosti s názvem closeButton](../ide/media/express_setnameproperty.png)<br>***Okno Vlastnosti*** *s* *názvem* ***closeButton***

    > [!NOTE]
    > Zkuste změnit název tlačítka a **zavřete tlačítko**s mezerou mezi slovy "zavřít" a "Tlačítko". Pokud tak učiníte, ide zobrazí chybovou zprávu: "Hodnota vlastnosti není platná." Mezery (a několik dalších znaků) nejsou povoleny v názvech ovládacích prvků.

1. Přejmenujte ostatní tři tlačítka na **backgroundButton**, **clearButton**a **showButton**.
Názvy můžete ověřit výběrem rozevíracího seznamu pro výběr ovládacích prvků v okně **Vlastnosti.** Zobrazí se nové názvy tlačítek.

1. Poklepejte na tlačítko **Zobrazit obrázek** ve formuláři. Jako alternativu zvolte tlačítko **Zobrazit obrázek** ve formuláři a stiskněte klávesu **Enter.** Když tak učiníte, ide otevře další kartu v hlavním okně s názvem **Form1.cs**. (Pokud používáte visual basic, karta se nazývá **Form1.vb).**

   Na této kartě se zobrazí soubor kódu za formulářem, jak je znázorněno na následujícím snímku obrazovky.

    ![Karta Form1.cs s kódem&#35; Visual C](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs*** *karta s kódem Jazyka C#*

    > [!NOTE]
    > Karta Form1.cs nebo Form1.vb může místo toho zobrazit **funkci showButton** jako **ShowButton.**

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

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Díváte se na `showButton_Click()` kód s `ShowButton_Click()`názvem (alternativně, ). IDE to toto přidalo do kódu formuláře při otevření souboru kódu pro tlačítko **showButton.** V době návrhu při otevření souboru kódu pro ovládací prvek ve formuláři je pro ovládací prvek generován kód, pokud ještě neexistuje. Tento kód, známý jako *metoda*, se spustí při spuštění aplikace a zvolte ovládací prvek – v tomto případě tlačítko **Zobrazit obrázek.**

1. Znovu zvolte kartu **Návrhář e-Windows Forms** Designer (**Form1.cs [Design]**) a pak otevřete soubor kódu pro tlačítko **Vymazat obrázek** a vytvořte pro ni metodu v kódu formuláře. Tento postup opakujte pro zbývající dvě tlačítka. Pokaždé, když ide přidá novou metodu do souboru kódu formuláře.

1. Chcete-li přidat ještě jednu metodu, otevřete soubor kódu pro ovládací `checkBox1_CheckedChanged()` prvek **CheckBox** v **Návrháři formulářů systému Windows,** aby ide přidat metodu. Tato metoda je volána vždy, když uživatel vybere nebo zruší zaškrtnutí políčka.

   > [!TIP]
   > Při práci na aplikaci se často přesouváte mezi editorem kódu a **Návrhářem formulářů Windows**. IDE usnadňuje navigaci v projektu. Pomocí **Průzkumníka řešení** otevřete **Návrháře formulářů systému Windows** poklepáním *Form1.cs* v jazyce C# nebo *Form1.vb* v jazyce Visual Basic nebo na řádku nabídek zvolte **Zobrazit** > **Návrháře**.

    V následujícím textu je uveden nový kód, který se zobrazí v editoru kódu.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Váš kód nemusí zobrazovat obslužné rutiny událostí v "camelCase" písmena.

    Pět metod, které jste přidali, se nazývá *obslužné rutiny událostí*, protože aplikace volá vždy, když dojde k události (například uživatel, který vybere tlačítko nebo vybere pole).

    Při zobrazení kódu pro ovládací prvek v ide v době návrhu Visual Studio přidá metodu obslužné rutiny události pro ovládací prvek, pokud není k dispozici. Například když poklepete na tlačítko, ide přidá obslužnou rutinu události pro jeho <xref:System.Windows.Forms.Control.Click> událost (která je volána vždy, když uživatel zvolí tlačítko). Po poklepání na zaškrtávací políčko přidá <xref:System.Windows.Forms.CheckBox.CheckedChanged> ide obslužnou rutinu události pro svou událost (která je volána vždy, když uživatel vybere nebo vymaže políčko).

    Po přidání obslužné rutiny události pro ovládací prvek se k němu můžete kdykoli vrátit z **Návrháře formulářů systému Windows** poklepáním na ovládací prvek nebo na řádku nabídek a výběrem **možnosti Zobrazit** > **kód**.

    Názvy jsou důležité při vytváření programů a metody (včetně obslužných rutin událostí) mohou mít libovolný název, který chcete. Přidáte-li obslužnou rutinu události s ide, vytvoří název na základě názvu ovládacího prvku a události, která je zpracovávána.

    Například Událost Click pro tlačítko s názvem `showButton_Click()` **showButton** se `ShowButton_Click()`nazývá metoda obslužné rutiny události (alternativně) . Také otevírání a zavírání `()` závorky jsou obvykle přidány za název metody označující, že metody jsou diskutovány.

    Pokud se rozhodnete změnit název kódové proměnné, klikněte pravým tlačítkem myši na proměnnou v kódu a pak zvolte **Přejmenovat refaktorování** > **Rename**. Všechny instance této proměnné v kódu jsou přejmenovány. Další informace naleznete [v tématu Rename refactoring](../ide/reference/rename.md).

## <a name="next-steps"></a>Další kroky

* Další krok kurzu najdete v **[tématu Krok 7: Přidání součástí dialogového okna do formuláře](../ide/step-7-add-dialog-components-to-your-form.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si následující krok 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
