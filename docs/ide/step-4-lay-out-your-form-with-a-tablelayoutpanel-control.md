---
title: 'Krok 4: Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579381"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4: Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel

V tomto kroku přidáte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek do formuláře. TableLayoutPanel pomáhá správně zarovnat ovládací prvky ve formuláři, který přidáte později.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Jak rozložit formulář pomocí ovládacího prvku TableLayoutPanel

1. Na levé straně prostředí IDE sady Visual Studio zvolte kartu **View** > **Toolbox** **Ctrl**+**Alt**+**X** **Panel nástrojů.**

1. Zvolte symbol malého trojúhelníku vedle **skupiny Kontejnery,** abyste ho otevřeli, jak je znázorněno na následujícím snímku obrazovky.

     ![Skupina kontejnerů](../ide/media/express_toolbox.png)<br>
***Skupina kontejnerů*** *group*

1. Do formuláře můžete přidat ovládací prvky, jako jsou tlačítka, zaškrtávací políčka a popisky. Poklepejte na ovládací prvek TableLayoutPanel v **panelu nástrojů**. (Nebo můžete ovládací prvek přetáhnout z panelu nástrojů do formuláře.) Když toto uděláte, ide přidá TableLayoutPanel ovládací prvek do formuláře, jak je znázorněno na následujícím snímku obrazovky.

     ![Ovládací prvek TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***Ovládací prvek TableLayoutPanel*** *control*

    > [!NOTE]
    > Po přidání panelu TableLayoutPanel se pokud se ve formuláři zobrazí okno s názvem **TableLayoutPanel Tasks**, zvolte libovolné místo ve formuláři a zavřete jej. Další informace o tomto okně se dozvíte později v kurzu.

     Všimněte si, jak se **panel nástrojů** rozbalí tak, aby pokrýval váš formulář, když zvolíte jeho kartu, a zavře se poté, co vyberete kdekoli mimo něj. To je funkce Automatické skrytí v ide. Můžete jej zapnout nebo vypnout pro libovolné z oken výběrem ikony připínáčku v pravém horním rohu okna pro přepnutí automatického skrytí a jeho uzamčení na místě. Ikona připínáčku se zobrazí následujícím způsobem.

     ![Ikona připínáčku](../ide/media/express_pushpintoolbox.png)<br>
*Ikona* ***připínáčku***

1. Ujistěte se, že TableLayoutPanel je vybrán a to výběrem. Jaký ovládací prvek je vybrán, můžete ověřit tak, že se podíváte do rozevíracího seznamu v horní části okna **Vlastnosti,** jak je znázorněno na následujícím snímku obrazovky.

     ![Okno Vlastnosti s ovládacím prvkem TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Okno Vlastnosti*** *s ovládacím* *prvkem* ***TableLayoutPanel***

1. Zvolte **abecední** tlačítko na panelu nástrojů v okně **Vlastnosti.** To seřadí seznam vlastností v okně **Vlastnosti** v abecedním pořadí, což usnadňuje vyhledání vlastností v tomto kurzu.

1. Volič ovládacího prvku je rozevírací seznam v horní části okna **Vlastnosti.** V tomto příkladu ukazuje, `tableLayoutPanel1` že je vybrán ovládací prvek volaný. Ovládací prvky můžete vybrat buď výběrem oblasti v **Návrháři formulářů systému Windows,** nebo výběrem z ovládacího prvku.

   Teď, když je vybraná volba TableLayoutPanel, najděte vlastnost **Dock** a zvolte **Dock**, který by měl být nastaven na **žádný**. Všimněte si, že se vedle hodnoty zobrazí šipka rozevíracího seznamu. Zvolte šipku a pak vyberte tlačítko **Vyplnit** (velké tlačítko uprostřed), jak je znázorněno na následujícím snímku obrazovky.

     ![Okno Vlastnosti s vybranou výplní](../ide/media/express_docktable.png)<br>
***Okno Vlastnosti*** *s vybranou* ***výplní*** *selected*

     *Ukotvení* v sadě Visual Studio označuje, když je okno připojeno k jinému oknu nebo oblasti v prostředí IDE. Například **vlastnosti** okno může být&mdash;undocked, který je nepřipojený&mdash;a volně plovoucí v rámci sady Visual Studio nebo může být ukotven a **explorer řešení**.

1. Po nastavení vlastnosti TableLayoutPanel **Dock** na **Fill**si všimněte, že panel vyplňuje celý formulář. Pokud změníte velikost formuláře znovu, TableLayoutPanel zůstane ukotvený a změní velikost sám tak, aby se vešly.

    > [!NOTE]
    > TableLayoutPanel funguje jako tabulka v aplikaci Microsoft Office Word: Má řádky a sloupce a jednotlivé buňky mohou přesahovat více řádků a sloupců. Každá buňka může obsahovat jeden ovládací prvek (například tlačítko, zaškrtávací políčko nebo popisek). TableLayoutPanel by měl <xref:System.Windows.Forms.PictureBox> mít ovládací prvek zahrnující celý <xref:System.Windows.Forms.CheckBox> jeho horní řádek, ovládací <xref:System.Windows.Forms.Button> prvek v jeho levé dolní buňky a čtyři ovládací prvky v jeho pravé dolní buňky.

1. V současné době TableLayoutPanel má dva řádky stejné velikosti a dva sloupce stejné velikosti. Změňte jejich velikost tak, aby horní řádek a pravý sloupec byly mnohem větší. V **Návrháři formulářů systému Windows**vyberte panel TableLayoutPanel. V pravém horním rohu je malé černé trojúhelníkové tlačítko, které se zobrazí následujícím způsobem.

     ![Tlačítko Trojúhelník](../ide/media/express_iconblacktriangle.gif)<br>
***Tlačítko Trojúhelník*** *button*

     Toto tlačítko označuje, že ovládací prvek má úkoly, které vám pomohou nastavit jeho vlastnosti automaticky.

1. Zvolte trojúhelník, chcete-li zobrazit seznam úkolů ovládacího prvku, jak je znázorněno na následujícím snímku obrazovky.

     ![Úkoly TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Úkoly TableLayoutPanel*** *tasks*

1. Zvolte úkol **Upravit řádky a sloupce,** chcete-li zobrazit okno **Styly sloupců a řádků.** Zvolte **Sloupec1**a nastavte jeho velikost na 15 procent tím, že se ujistěte, že je vybráno tlačítko **Procento** a zadáte **15** do pole **Procento.** (To je <xref:System.Windows.Forms.NumericUpDown> ovládací prvek, který budete používat v pozdějším kurzu.) Zvolte **Sloupec2** a nastavte jej na 85 procent. Tlačítko **OK** zatím nevybírejte, protože okno se zavře. (Pokud tak však učiníte, můžete jej znovu otevřít pomocí seznamu úkolů.)

     ![TableLayoutStyly sloupců a řádků panelu](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutStyly*** *sloupců a řádků panelu*

1. V rozevíracím seznamu **Zobrazit** v horní části okna **Styly sloupců a řádků** zvolte **Řádky**. Nastavte **řádek1** na 90 procent a **řádek2** na 10 procent.

1. Zvolte tlačítko **OK.** TableLayoutPanel by nyní měl mít velký horní řádek, malý dolní řádek, malý levý sloupec a velký pravý sloupec. (Velikost řádků a sloupců v panelu TableLayoutpanel můžete změnit výběrem **tableLayoutPanel1** ve formuláři a přetažením ohraničení řádků a sloupců.)

     ![Formulář1 se změnou velikosti TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)<br>
***Formulář1*** *(Prohlížeč obrázků) s rozložením* ***tabulky***

## <a name="next-steps"></a>Další kroky

* Další krok kurzu najdete v **[tématu Krok 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si následující krok 3: Nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
