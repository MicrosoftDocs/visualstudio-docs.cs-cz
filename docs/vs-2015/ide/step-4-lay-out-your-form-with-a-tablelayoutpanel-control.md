---
title: 'Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54e4713abef096d5a23cf1ebf74a9d90db0d6409
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295735"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4: Rozvrhněte svůj formulář pomocí ovládacího prvku TableLayoutPanel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku přidáte ovládací prvek `TableLayoutPanel` do formuláře. Kontejner TableLayoutPanel pomáhá správně zarovnat ovládací prvky ve formuláři, který budete přidávat později.

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-video 2](https://go.microsoft.com/fwlink/?LinkId=205211) nebo v [kurzu 1: vytvoření prohlížeče obrázků ve C# videu 2](https://go.microsoft.com/fwlink/?LinkId=205200). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel

1. Na levé straně integrovaného vývojového prostředí sady Visual Studio Najděte kartu **panel nástrojů** . Vyberte kartu **panel nástrojů** a zobrazí se panel nástrojů. (Nebo, na panelu nabídek vyberte možnost **zobrazení**, **Sada nástrojů**.)

2. Vyberte symbol malého trojúhelníku vedle skupiny **kontejnery** a otevřete ho tak, jak je znázorněno na následujícím obrázku.

     ![Skupina kontejnerů](../ide/media/express-toolbox.png "Express_Toolbox") Skupina kontejnerů

3. Do formuláře můžete přidat ovládací prvky, jako jsou tlačítka, zaškrtávací políčka a popisky. Dvakrát klikněte na ovládací prvek `TableLayoutPanel` v sadě nástrojů. (Nebo můžete přetáhnout ovládací prvek z panelu nástrojů do formuláře.) Když to uděláte, rozhraní IDE přidá ovládací prvek `TableLayoutPanel` do formuláře, jak je znázorněno na následujícím obrázku.

     ![TableLayoutPanel – ovládací prvek](../ide/media/express-formtablelayout.png "Express_FormTableLayout") TableLayoutPanel – ovládací prvek

    > [!NOTE]
    > Po přidání kontejneru TableLayoutPanel, pokud se zobrazí okno v rámci formuláře s názvem **úlohy TableLayoutPanel**, vyberte libovolné místo ve formuláři a zavřete ho. Další informace o tomto okně se dozvíte později v tomto kurzu.

     Všimněte si, jak se sada nástrojů rozšíří na pokrytí formuláře, když zvolíte jeho kartu a po výběru kamkoli mimo ni se zavře. To je funkce automatického skrývání rozhraní IDE. Můžete ji zapnout nebo vypnout pro kterékoli z oken tak, že vyberete ikonu připínáčku v pravém horním rohu okna a vypnete automatické skrývání a zamknete ho. Ikona připínáček se zobrazí takto.

     ![Ikona připínáček](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox") Ikona připínáček

4. Ujistěte se, že je **kontejner TableLayoutPanel** vybrán výběrem. Vybraný ovládací prvek můžete ověřit tak, že prohlížíte rozevírací seznam v horní části okna **vlastnosti** , jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti znázorňující ovládací prvek TableLayoutPanel](../ide/media/express-controlspropwin.png "Express_ControlsPropWin") okno Vlastnosti znázorňující ovládací prvek TableLayoutPanel

5. Na panelu nástrojů v okně **vlastnosti** vyberte tlačítko **Abecední** . To způsobí, že se seznam vlastností v okně **vlastnosti** zobrazí v abecedním pořadí, což usnadňuje hledání vlastností v tomto kurzu.

6. Selektor ovládacího prvku je rozevírací seznam v horní části okna **vlastnosti** . V tomto příkladu ukazuje, že je vybrán ovládací prvek s názvem `tableLayoutPanel1`. Ovládací prvky můžete vybrat buď výběrem oblasti v Návrhář formulářů, nebo výběrem z voliče ovládacího prvku. Teď, když je vybraná `TableLayoutPanel`, Najděte vlastnost **Dock** a vyberte **Dock**, která by měla být nastavená na **None (žádné**). Všimněte si, že se vedle hodnoty zobrazí šipka rozevíracího seznamu. Zvolte šipku a potom vyberte tlačítko **vyplnit** (velké tlačítko uprostřed), jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti s vybraným vyplněním](../ide/media/express-docktable.png "Express_DockTable") okno Vlastnosti s vybraným vyplněním

     *Ukotvení* v aplikaci Visual Studio odkazuje na to, kdy je okno připojeno k jinému oknu nebo oblasti v rozhraní IDE. Například okno Vlastnosti může být nedocked – to znamená, nepřipojené a bezplatné v rámci sady Visual Studio – nebo může být ukotveno proti **Průzkumník řešení**.

7. Jakmile nastavíte vlastnost **Dock** kontejneru TableLayoutPanel na hodnotu **Fill**, panel vyplní celý formulář. Pokud změníte velikost formuláře znovu, kontejner TableLayoutPanel zůstane ukotvený a mění se tak, aby odpovídal.

    > [!NOTE]
    > Kontejner TableLayoutPanel funguje jako tabulka v systém Microsoft Office Wordu: má řádky a sloupce a jednotlivé buňky mohou zahrnovat více řádků a sloupců. Každá buňka může obsahovat jeden ovládací prvek (například tlačítko, zaškrtávací políčko nebo popisek). Váš kontejner TableLayoutPanel bude mít ovládací prvek `PictureBox` rozložený do celého horního řádku, `CheckBox` ovládacího prvku v jeho spodní buňce vlevo a čtyři ovládací prvky `Button` v její dolní pravé buňce.

8. V současné době má kontejner TableLayoutPanel dva řádky stejné velikosti a dva sloupce se stejnou velikostí. Je potřeba změnit jejich velikost, aby horní řádek a pravý sloupec byly mnohem větší. V Návrhář formulářů vyberte kontejner TableLayoutPanel. V pravém horním rohu je malé černé trojúhelníkové tlačítko, které se zobrazí takto.

     ![Tlačítko trojúhelníku](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle") Tlačítko trojúhelníku

     Toto tlačítko indikuje, že ovládací prvek obsahuje úlohy, které vám pomůžou nastavit jeho vlastnosti automaticky.

9. Vyberte trojúhelník pro zobrazení seznamu úkolů ovládacího prvku, jak je znázorněno na následujícím obrázku.

     ![Úlohy TableLayoutPanel](../ide/media/express-tablepanel.png "Express_TablePanel") Úlohy TableLayoutPanel

10. Vyberte úlohu **Upravit řádky a sloupce** , aby se zobrazilo okno **styly sloupců a řádků** . Vyberte **sloupec Sloupe**a nastavte jeho velikost na 15 procent, a to tak, že vyberete tlačítko **procento** a zadáte `15` do pole **procenta** . (Jedná se o ovládací prvek `NumericUpDown`, který budete používat v pozdějším kurzu.) Vyberte hodnotu **Sloupe** a nastavte ji na 85 procent. Nevybírejte ještě tlačítko **OK** , protože okno se zavře. (Pokud to ale uděláte, můžete ho znovu otevřít pomocí seznamu úkolů.)

     ![Styly sloupců a řádků TableLayoutPanel](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup") Styly sloupců a řádků TableLayoutPanel

11. V rozevíracím seznamu **Zobrazit** v horní části okna vyberte možnost **řádky**. Nastavte **řádek1** na 90 procent a **řádek2** na 10 procent.

12. Klikněte na tlačítko **OK** . Váš kontejner TableLayoutPanel by teď měl mít velký horní řádek, malý dolní řádek, malý levý sloupec a velký pravý sloupec. Můžete změnit velikost řádků a sloupců v kontejneru TableLayoutPanel výběrem tableLayoutPanel1 ve formuláři a následným přetažením ohraničení jeho řádku a sloupce.

     ![Form1 se změněnou velikostí kontejneru TableLayoutPanel](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel") Form1 se změněnou velikostí kontejneru TableLayoutPanel

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 3: nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md).
