---
title: Rozvržení formuláře pomocí ovládacího prvku TableLayoutPanel
description: Rozložte formulář pomocí ovládacího prvku TableLayoutPanel v kurzu Vytvoření prohlížeče obrázků.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 06918ccdefdd18109b4e34c373bda75defa2a81b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950689"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4: Rozvržení formuláře pomocí ovládacího prvku TableLayoutPanel

V tomto kroku přidáte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek do formuláře. Kontejner TableLayoutPanel pomáhá správně zarovnat ovládací prvky ve formuláři, který později přidáte.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Postup rozložení formuláře pomocí ovládacího prvku TableLayoutPanel

1. Na levé straně integrovaného vývojového prostředí sady Visual Studio zvolte kartu **panel nástrojů** . (případně zvolte možnost **Zobrazit**  >  **sadu nástrojů** na panelu nabídek nebo stiskněte klávesu **CTRL** + **ALT** + **X**.)

1. Vyberte symbol malého trojúhelníku vedle skupiny **kontejnery** a otevřete ho tak, jak je znázorněno na následujícím snímku obrazovky.

     ![Skupina kontejnerů](../ide/media/express_toolbox.png)<br>
***Kontejnery** _ _group *

1. Do formuláře můžete přidat ovládací prvky, jako jsou tlačítka, zaškrtávací políčka a popisky. Dvakrát klikněte na ovládací prvek TableLayoutPanel v **sadě nástrojů**. (Nebo můžete přetáhnout ovládací prvek z panelu nástrojů do formuláře.) Když to uděláte, rozhraní IDE přidá ovládací prvek TableLayoutPanel do formuláře, jak je znázorněno na následujícím snímku obrazovky.

     ![TableLayoutPanel – ovládací prvek](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel** _ _Control *

    > [!NOTE]
    > Po přidání kontejneru TableLayoutPanel, pokud se zobrazí okno v rámci formuláře s názvem **úlohy TableLayoutPanel**, vyberte libovolné místo ve formuláři a zavřete ho. Další informace o tomto okně se dozvíte později v tomto kurzu.

     Všimněte si, jak se **Sada nástrojů** rozšíří na pokrytí formuláře, když zvolíte jeho kartu a po výběru kamkoli mimo ni se zavře. To je funkce automatického skrývání v integrovaném vývojovém prostředí. Můžete ji zapnout nebo vypnout pro kterékoli z oken tak, že vyberete ikonu připínáčku v pravém horním rohu okna a vypnete automatické skrývání a zamknete ho. Ikona připínáček se zobrazí takto.

     ![Ikona připínáček](../ide/media/express_pushpintoolbox.png)<br>
***Připínáček** _ _icon *

1. Ujistěte se, že je kontejner TableLayoutPanel vybrán výběrem. Vybraný ovládací prvek můžete ověřit tak, že prohlížíte rozevírací seznam v horní části okna **vlastnosti** , jak je znázorněno na následujícím snímku obrazovky.

     ![okno Vlastnosti znázorňující ovládací prvek TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Properties** _ _okno zobrazující * ***TableLayoutPanel**_ _Control *

1. Na panelu nástrojů v okně **vlastnosti** vyberte tlačítko **Abecední** . Tím se seřadí seznam vlastností v okně **vlastnosti** v abecedním pořadí, což usnadňuje hledání vlastností v tomto kurzu.

1. Selektor ovládacího prvku je rozevírací seznam v horní části okna **vlastnosti** . V tomto příkladu ukazuje, že je vybrán ovládací prvek s názvem `tableLayoutPanel1` . Ovládací prvky můžete vybrat buď výběrem oblasti v **Návrhář formulářů** , nebo výběrem z voliče ovládacího prvku.

   Teď, když je vybraný kontejner TableLayoutPanel, Najděte vlastnost **Dock** a vyberte **Dock**, která by měla být nastavená na **none**. Všimněte si, že se vedle hodnoty zobrazí šipka rozevíracího seznamu. Zvolte šipku a potom vyberte tlačítko **vyplnit** (velké tlačítko uprostřed), jak je znázorněno na následujícím snímku obrazovky.

     ![okno Vlastnosti s vybraným vyplněním](../ide/media/express_docktable.png)<br>
***Properties** _ _Window s * ***Fill**_ _selected *

     *Ukotvení* v aplikaci Visual Studio odkazuje na to, kdy je okno připojeno k jinému oknu nebo oblasti v rozhraní IDE. Například může být okno **vlastnosti** nedocked &mdash; , tj. nepřipojené a bezplatné – plovoucí v rámci sady Visual Studio, &mdash; nebo může být ukotveno proti **Průzkumník řešení**.

1. Jakmile nastavíte vlastnost **Dock** kontejneru TableLayoutPanel na hodnotu **Fill**, Všimněte si, že panel vyplní celý formulář. Pokud změníte velikost formuláře znovu, kontejner TableLayoutPanel zůstane ukotvený a mění se tak, aby odpovídal.

    > [!NOTE]
    > Kontejner TableLayoutPanel funguje jako tabulka v systém Microsoft Office Wordu: má řádky a sloupce a jednotlivé buňky mohou zahrnovat více řádků a sloupců. Každá buňka může obsahovat jeden ovládací prvek (například tlačítko, zaškrtávací políčko nebo popisek). Váš kontejner TableLayoutPanel by měl mít <xref:System.Windows.Forms.PictureBox> ovládací prvek rozložený do celého horního řádku, <xref:System.Windows.Forms.CheckBox> ovládací prvek v jeho spodní buňce vlevo a čtyři <xref:System.Windows.Forms.Button> ovládací prvky v jeho pravé dolní buňce.

1. V současné době má kontejner TableLayoutPanel dva řádky stejné velikosti a dva sloupce se stejnou velikostí. Umožňuje změnit jejich velikost, takže horní řádek a pravý sloupec budou mnohem větší. V **Návrhář formulářů** vyberte kontejner TableLayoutPanel. V pravém horním rohu je malé černé trojúhelníkové tlačítko, které se zobrazí takto.

     ![Tlačítko trojúhelníku](../ide/media/express_iconblacktriangle.gif)<br>
***Trojúhelník** _ _button *

     Toto tlačítko indikuje, že ovládací prvek obsahuje úlohy, které vám pomůžou nastavit jeho vlastnosti automaticky.

1. Vyberte trojúhelník pro zobrazení seznamu úkolů ovládacího prvku, jak je znázorněno na následujícím snímku obrazovky.

     ![Úlohy TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel** _ _tasks *

1. Vyberte úlohu **Upravit řádky a sloupce** , aby se zobrazilo okno **styly sloupců a řádků** . Vyberte **sloupec Sloupec1** a nastavte jeho velikost na 15 procent, a to tak, že vyberete tlačítko **procento** a do pole **procenta** zadáte **15** . (To je <xref:System.Windows.Forms.NumericUpDown> ovládací prvek, který budete používat v pozdějším kurzu.) Vyberte hodnotu **Sloupec2** a nastavte ji na 85 procent. Nevybírejte ještě tlačítko **OK** , protože okno se zavře. (Pokud to ale uděláte, můžete ho znovu otevřít pomocí seznamu úkolů.)

     ![Styly sloupců a řádků TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel** _ _column a styly řádků *

1. V rozevíracím seznamu **Zobrazit** v horní části okna **a styly řádků** vyberte možnost **řádky**. Nastavte **řádek1** na 90 procent a **řádek2** na 10 procent.

1. Klikněte na tlačítko **OK** . Váš kontejner TableLayoutPanel by teď měl mít velký horní řádek, malý dolní řádek, malý levý sloupec a velký pravý sloupec. (Můžete změnit velikost řádků a sloupců v kontejneru TableLayoutPanel výběrem **tableLayoutPanel1** ve formuláři a následným přetažením ohraničení jeho řádku a sloupce.)

     ![Form1 se změněnou velikostí kontejneru TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1** _ _ (prohlížeč obrázků) se změněnou velikostí * ***TableLayoutPanel***

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si **[článek 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md)**.

* Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 3: nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
