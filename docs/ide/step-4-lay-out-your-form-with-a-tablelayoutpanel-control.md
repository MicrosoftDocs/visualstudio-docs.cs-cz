---
title: 'Krok 4: Rozvržení formuláře pomocí ovládacího prvku TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3595705030e2e969f99455700ab70f36bf22274a
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887982"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4: Rozvržení formuláře pomocí ovládacího prvku TableLayoutPanel

V tomto kroku přidáte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek do formuláře. Kontejner TableLayoutPanel pomáhá správně zarovnat ovládací prvky ve formuláři, který později přidáte.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Postup rozložení formuláře pomocí ovládacího prvku TableLayoutPanel

1. Na levé straně integrovaného vývojového prostředí sady Visual Studio vyberte kartu **panel nástrojů** . (Případně zvolte možnost **Zobrazit** > **sadu nástrojů** z panelu nabídek nebo stiskněte klávesu **CTRL**+**ALT**+**X**.)

1. Vyberte symbol malého trojúhelníku vedle skupiny **kontejnery** a otevřete ho tak, jak je znázorněno na následujícím snímku obrazovky.

     ![Skupina kontejnerů](../ide/media/express_toolbox.png)<br>
***Kontejnery*** *Skupina*

1. Do formuláře můžete přidat ovládací prvky, jako jsou tlačítka, zaškrtávací políčka a popisky. Dvakrát klikněte na ovládací prvek TableLayoutPanel v **sadě nástrojů**. (Nebo můžete přetáhnout ovládací prvek z panelu nástrojů do formuláře.) Když to uděláte, rozhraní IDE přidá ovládací prvek TableLayoutPanel do formuláře, jak je znázorněno na následujícím snímku obrazovky.

     ![TableLayoutPanel – ovládací prvek](../ide/media/express_formtablelayout.png)<br>
***Kontejner TableLayoutPanel*** *ovládací prvek*

    > [!NOTE]
    > Po přidání kontejneru TableLayoutPanel, pokud se zobrazí okno v rámci formuláře s názvem **úlohy TableLayoutPanel**, vyberte libovolné místo ve formuláři a zavřete ho. Další informace o tomto okně se dozvíte později v tomto kurzu.

     Všimněte si, jak se **Sada nástrojů** rozšíří na pokrytí formuláře, když zvolíte jeho kartu a po výběru kamkoli mimo ni se zavře. To je funkce automatického skrývání v integrovaném vývojovém prostředí. Můžete ji zapnout nebo vypnout pro kterékoli z oken tak, že vyberete ikonu připínáčku v pravém horním rohu okna a vypnete automatické skrývání a zamknete ho. Ikona připínáček se zobrazí takto.

     ![Ikona připínáček](../ide/media/express_pushpintoolbox.png)<br>
***Připínáček*** *ikona*

1. Ujistěte se, že je kontejner TableLayoutPanel vybrán výběrem. Vybraný ovládací prvek můžete ověřit tak, že prohlížíte rozevírací seznam v horní části okna **vlastnosti** , jak je znázorněno na následujícím snímku obrazovky.

     ![okno Vlastnosti znázorňující ovládací prvek TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Vlastnosti*** *okno zobrazující* ***Kontejner TableLayoutPanel*** *ovládací prvek*

1. Na panelu nástrojů v okně **vlastnosti** vyberte tlačítko **Abecední** . Tím se seřadí seznam vlastností v okně **vlastnosti** v abecedním pořadí, což usnadňuje hledání vlastností v tomto kurzu.

1. Selektor ovládacího prvku je rozevírací seznam v horní části okna **vlastnosti** . V tomto příkladu ukazuje, že je vybrán ovládací prvek `tableLayoutPanel1` s názvem. Ovládací prvky můžete vybrat buď výběrem oblasti v **Návrhář formulářů** , nebo výběrem z voliče ovládacího prvku.

   Teď, když je vybraný kontejner TableLayoutPanel, Najděte vlastnost **Dock** a vyberte **Dock**, která by měla být nastavená na **none**. Všimněte si, že se vedle hodnoty zobrazí šipka rozevíracího seznamu. Zvolte šipku a potom vyberte tlačítko **vyplnit** (velké tlačítko uprostřed), jak je znázorněno na následujícím snímku obrazovky.

     ![okno Vlastnosti s vybraným vyplněním](../ide/media/express_docktable.png)<br>
***Vlastnosti*** *okno s* ***Vyplnit*** *Vybraná možnost*

     *Ukotvení* v aplikaci Visual Studio odkazuje na to, kdy je okno připojeno k jinému oknu nebo oblasti v rozhraní IDE. Například může být okno **vlastnosti** nedocked&mdash;, tj. nepřipojené a bezplatné – plovoucí v rámci sady Visual Studio&mdash;, nebo může být ukotveno proti **Průzkumník řešení**.

1. Jakmile nastavíte vlastnost **Dock** kontejneru TableLayoutPanel na hodnotu **Fill**, Všimněte si, že panel vyplní celý formulář. Pokud změníte velikost formuláře znovu, kontejner TableLayoutPanel zůstane ukotvený a mění se tak, aby odpovídal.

    > [!NOTE]
    > TableLayoutPanel funguje jako tabulka v systém Microsoft Office Word: Má řádky a sloupce a jednotlivá buňka může zahrnovat více řádků a sloupců. Každá buňka může obsahovat jeden ovládací prvek (například tlačítko, zaškrtávací políčko nebo popisek). Váš kontejner TableLayoutPanel by měl <xref:System.Windows.Forms.PictureBox> mít ovládací prvek rozložený do celého horního řádku <xref:System.Windows.Forms.CheckBox> , ovládací prvek v jeho spodní buňce vlevo <xref:System.Windows.Forms.Button> a čtyři ovládací prvky v jeho pravé dolní buňce.

1. V současné době má kontejner TableLayoutPanel dva řádky stejné velikosti a dva sloupce se stejnou velikostí. Umožňuje změnit jejich velikost, takže horní řádek a pravý sloupec budou mnohem větší. V **Návrhář formulářů**vyberte kontejner TableLayoutPanel. V pravém horním rohu je malé černé trojúhelníkové tlačítko, které se zobrazí takto.

     ![Tlačítko trojúhelníku](../ide/media/express_iconblacktriangle.gif)<br>
***Trojúhelník*** *tlačítko*

     Toto tlačítko indikuje, že ovládací prvek obsahuje úlohy, které vám pomůžou nastavit jeho vlastnosti automaticky.

1. Vyberte trojúhelník pro zobrazení seznamu úkolů ovládacího prvku, jak je znázorněno na následujícím snímku obrazovky.

     ![Úlohy TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Kontejner TableLayoutPanel*** *úkoly*

1. Vyberte úlohu **Upravit řádky a sloupce** , aby se zobrazilo okno **styly sloupců a řádků** . Vyberte **sloupec Sloupec1**a nastavte jeho velikost na 15 procent, a to tak, že vyberete tlačítko **procento** a do pole **procenta** zadáte **15** . (To <xref:System.Windows.Forms.NumericUpDown> je ovládací prvek, který budete používat v pozdějším kurzu.) Vyberte hodnotu **Sloupec2** a nastavte ji na 85 procent. Nevybírejte ještě tlačítko **OK** , protože okno se zavře. (Pokud to ale uděláte, můžete ho znovu otevřít pomocí seznamu úkolů.)

     ![Styly sloupců a řádků TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***Kontejner TableLayoutPanel*** *styly sloupců a řádků*

1. V rozevíracím seznamu **Zobrazit** v horní části okna **a styly řádků** vyberte možnost **řádky**. Nastavte **řádek1** na 90 procent a **řádek2** na 10 procent.

1. Zvolte **OK** tlačítko. Váš kontejner TableLayoutPanel by teď měl mít velký horní řádek, malý dolní řádek, malý levý sloupec a velký pravý sloupec. (Můžete změnit velikost řádků a sloupců v kontejneru TableLayoutPanel výběrem **tableLayoutPanel1** ve formuláři a následným přetažením ohraničení jeho řádku a sloupce.)

     ![Form1 se změněnou velikostí kontejneru TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Prohlížeč obrázků) se změněnou velikostí* ***Kontejner TableLayoutPanel***

## <a name="next-steps"></a>Další postup

* Pokud chcete přejít na další krok kurzu, přečtěte si  **[krok 5: Přidejte ovládací prvky do formuláře](../ide/step-5-add-controls-to-your-form.md).**

* Pokud se chcete vrátit k předchozímu kroku kurzu [, podívejte se na krok 3: Nastavte vlastnosti](../ide/step-3-set-your-form-properties.md)formuláře.

## <a name="see-also"></a>Viz také:

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: Vytvořit porovnávací hru](tutorial-3-create-a-matching-game.md)
