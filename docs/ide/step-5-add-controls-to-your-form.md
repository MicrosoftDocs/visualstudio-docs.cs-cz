---
title: 'Krok 5: Přidání ovládacích prvků do formuláře'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579363"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Přidání ovládacích prvků do formuláře

V tomto kroku přidáte ovládací prvky, například <xref:System.Windows.Forms.PictureBox> ovládací prvek a <xref:System.Windows.Forms.CheckBox> ovládací prvek, do formuláře. Pak přidáte <xref:System.Windows.Forms.Button> ovládací prvky do formuláře.

## <a name="how-to-add-controls-to-your-form"></a>Postup přidání ovládacích prvků do formuláře

1. Zvolte kartu **panel nástrojů** na levé straně integrovaného vývojového prostředí sady Visual Studio (nebo stiskněte klávesu **CTRL** + **ALT** + **X**) a potom rozbalte skupinu **běžných ovládacích prvků** . Tím se zobrazí nejběžnější ovládací prvky, které vidíte ve formulářích.

1. Dvojím kliknutím na položku **PictureBox** přidáte ovládací prvek PictureBox do formuláře. Vzhledem k tomu, že kontejner TableLayoutPanel je ukotven pro vyplnění formuláře, rozhraní IDE přidá ovládací prvek PictureBox do první prázdné buňky (levý horní roh).

1. Zvolte nový ovládací prvek **PictureBox** , který chcete vybrat, a pak zvolte černý trojúhelník na novém ovládacím prvku PictureBox a zobrazte jeho seznam úkolů, jak je znázorněno na následujícím snímku obrazovky.

    ![Úlohy PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox * * * *úkoly**

    > [!NOTE]
    > Pokud omylem přidáte nesprávný typ ovládacího prvku do kontejneru TableLayoutPanel, můžete jej odstranit. Klikněte na ovládací prvek pravým tlačítkem myši a potom v místní nabídce vyberte možnost **Odstranit** . Ovládací prvky můžete odebrat také z formuláře pomocí panelu nabídek. Na panelu nabídek vyberte možnost **Upravit**  >  **zpět**nebo **Upravit**  >  **Odstranit**.

1. V nabídce **úkoly PictureBox** ovládacího prvku **PictureBox** vyberte odkaz **Dock v nadřazeném kontejneru** . Tím se automaticky nastaví vlastnost PictureBox **Dock** na **Fill**. Chcete-li se podívat, zvolte ovládací prvek **PictureBox** , který chcete vybrat, přejděte do okna **vlastnosti** a ujistěte se, že vlastnost **Dock** je nastavena na hodnotu **Fill**.

1. Nastavte, aby PictureBox rozspan oba sloupce změnou jeho vlastnosti **jeho ColumnSpan** . V ovládacím prvku **PictureBox**vyberte ovládací prvek **PictureBox** a nastavte jeho vlastnost **jeho ColumnSpan** na hodnotu **2**. Také, pokud je PictureBox prázdné, chcete zobrazit prázdný rámeček. Nastavte jeho vlastnost **BorderStyle** na **Fixed3D**.

    > [!NOTE]
    > Pokud nevidíte vlastnost **jeho ColumnSpan** ovládacího prvku PictureBox, je možné, že byl ovládací prvek PictureBox přidán do formuláře namísto kontejneru TableLayoutPanel. Chcete-li tento problém opravit, zvolte **PictureBox**, odstraňte jej, zvolte **kontejner TableLayoutPanel**a pak přidejte nový PictureBox.

1. Zvolte **kontejner TableLayoutPanel** ve formuláři a poté přidejte ovládací prvek CheckBox do formuláře. Dvojitým kliknutím na položku **CheckBox** v **sadě nástrojů** přidáte nový ovládací prvek CheckBox do další volné buňky v tabulce. Vzhledem k tomu, že PictureBox zabírá první dvě buňky v kontejneru TableLayoutPanel, ovládací prvek CheckBox se přidá do levé dolní buňky. Vyberte vlastnost **text** a zadejte slovo **roztáhnout**, jak je znázorněno na následujícím obrázku.

    ![Ovládací prvek TextBox s vlastností Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***TextBox*** *Ovládací prvek TextBox s* *vlastností* ***Stretch***

1. Zvolte **kontejner TableLayoutPanel** ve formuláři a potom přejděte do skupiny **kontejnery** v sadě **nástrojů** (kde jste získali svůj ovládací prvek TableLayoutPanel) a dvakrát klikněte na položku **FlowLayoutPanel** a přidejte do poslední buňky nový ovládací prvek (vpravo dole). Poté ukotvěte FlowLayoutPanel do kontejneru TableLayoutPanel. To lze provést buď výběrem možnosti **Dock v nadřazeném kontejneru** v seznamu úkolů černého trojúhelníku FlowLayoutPanel, nebo nastavením vlastnosti **Dock** prvku FlowLayoutPanel na hodnotu **Fill**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> je kontejner, který uspořádá jiné ovládací prvky na řádek, jeden po druhém. Když změníte velikost kontejneru FlowLayoutPanel, rozloží všechny jeho ovládací prvky na jeden řádek, pokud má místo k tomu. V opačném případě je uspořádá na řádcích, jeden nad druhou. <br/><br/>Tady použijete FlowLayoutPanel k uložení čtyř tlačítek. Pokud tlačítka při přidávání sebe navzájem najdou jinam, nezapomeňte před přidáním tlačítek vybrat FlowLayoutPanel. <br/><br/>(Obvykle každá buňka obsahuje pouze jeden ovládací prvek. V tomto příkladu obsahuje pravá dolní buňka kontejneru TableLayoutPanel čtyři ovládací prvky tlačítka. Proč?  Vzhledem k tomu, že FlowLayoutPanel je ovládací prvek kontejneru, což je ovládací prvek v buňce, která obsahuje jiné ovládací prvky.)

## <a name="to-add-buttons"></a>Přidání tlačítek

1. Vyberte nový FlowLayoutPanel, který jste přidali. Přejděte na **běžné ovládací prvky** v **sadě nástrojů** a dvojitým kliknutím na položku **tlačítka** přidejte ovládací prvek tlačítko s názvem **Button1** do kontejneru FlowLayoutPanel. Opakováním přidejte další tlačítko. Rozhraní IDE zjistí, že již existuje tlačítko s názvem **Button1** a volá další **Button2**.

1. Obvykle se další tlačítka přidávají pomocí **sady nástrojů**. Tentokrát zvolte možnost **Button2**a potom v řádku nabídek zvolte možnost **Upravit**  >  **kopii** (nebo stiskněte klávesu **CTRL** + **C**). V dalším kroku zvolte možnost **Upravit**  >  **vložení** z řádku nabídek (nebo stiskněte klávesu **CTRL** + **V**) a vložte kopii tlačítka. Nyní jej vložte znovu. Všimněte si, že rozhraní IDE přidá do kontejneru FlowLayoutPanel **Button3** a **Button4** .

    > [!NOTE]
    > Můžete zkopírovat a vložit libovolný ovládací prvek. Rozhraní IDE názvy a umístí nové ovládací prvky logickým způsobem. Pokud ovládací prvek vložíte do kontejneru, rozhraní IDE zvolí další logický prostor pro umístění.

1. Vyberte první tlačítko a nastavte jeho vlastnost **text** tak, aby **zobrazovala obrázek**. Potom nastavte vlastnosti **textu** dalších tří tlačítek pro **vymazání obrázku**, **Nastavení barvy pozadí**a **zavření**.

1. Pojďme dát tlačítkům a uspořádat je tak, aby se rovnaly na pravé straně panelu. Vyberte **FlowLayoutPanel** a podívejte se na jeho vlastnost **FlowDirection** . Změňte ji tak, aby byla nastavená na **RightToLeft**.

   Tlačítka by se měla zarovnat do pravé strany buňky a obrátit jejich pořadí tak, aby tlačítko **Zobrazit obrázek** bylo na pravé straně.

    > [!NOTE]
    > Pokud jsou tlačítka stále v nesprávném pořadí, můžete přetáhnout tlačítka kolem FlowLayoutPanel a změnit jejich uspořádání v libovolném pořadí. Můžete zvolit tlačítko a přetáhnout ho doleva nebo doprava.

1. Kliknutím na tlačítko **Zavřít** jej vyberte. Pokud pak chcete zvolit zbývající část tlačítek najednou, stiskněte a podržte klávesu **CTRL** a vyberte je.

   Po výběru všech tlačítek přejděte do okna **vlastnosti** a posuňte se k vlastnosti **AutoSize** . Tato vlastnost oznamuje tlačítku, aby se automaticky změnila velikost tak, aby odpovídala veškerému jeho textu. Nastavte na **hodnotu true**.

   Tlačítka by měla být teď správně velikostná a musí být ve správném pořadí. (Pokud jsou vybrána všechna čtyři tlačítka, můžete změnit všechny čtyři vlastnosti **AutoSize** současně.) Následující obrázek znázorňuje čtyři tlačítka.

    ![Prohlížeč obrázků se čtyřmi tlačítky](../ide/media/express_autosize.png)<br/>***Prohlížeč obrázků*** *se čtyřmi tlačítky*

1. Nyní spusťte program znovu, abyste viděli změny.

   Všimněte si, že tlačítka a zaškrtávací políčko ještě nic nedělají &mdash; , ale budou brzy.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

* Pokud chcete přejít na další krok kurzu, přejděte na **[Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
