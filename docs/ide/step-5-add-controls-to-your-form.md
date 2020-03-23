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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579363"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Přidání ovládacích prvků do formuláře

V tomto kroku přidáte do formuláře <xref:System.Windows.Forms.PictureBox> ovládací <xref:System.Windows.Forms.CheckBox> prvky, například ovládací prvek a ovládací prvek. Potom přidáte <xref:System.Windows.Forms.Button> ovládací prvky do formuláře.

## <a name="how-to-add-controls-to-your-form"></a>Přidání ovládacích prvků do formuláře

1. Zvolte kartu **Panel u nástrojů** na levé straně rozhraní IDE sady Visual Studio (nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**X**) a rozbalte skupinu Společné **ovládací prvky.** Zobrazí nejběžnější ovládací prvky, které se zobrazují ve formulářích.

1. Poklepáním na položku **PictureBox** přidejte do formuláře ovládací prvek PictureBox. Vzhledem k tomu, že TableLayoutPanel je ukotven k vyplnění formuláře, ide přidá ovládací prvek PictureBox do první prázdné buňky (levý horní roh).

1. Vyberte nový ovládací prvek **PictureBox** a pak zvolte černý trojúhelník na novém ovládacím prvku PictureBox, abyste zobrazili jeho seznam úkolů, jak je znázorněno na následujícím snímku obrazovky.

    ![Úlohy pictureboxu](../ide/media/express_pictureboxtasks.png)<br/>*Úlohy* PictureBoxu****

    > [!NOTE]
    > Pokud omylem přidáte nesprávný typ ovládacího prvku do panelu TableLayoutPanel, můžete jej odstranit. Klikněte pravým tlačítkem myši na ovládací prvek a v jeho kontextové nabídce zvolte **Odstranit.** Ovládací prvky můžete také odebrat z formuláře pomocí panelu nabídek. Na řádku nabídek zvolte **Upravit** > **vrátit se k ní**nebo **Upravit** > **odstranění**.

1. V nabídce **Úlohy obrázku** v ovládacím prvku **PictureBox** zvolte odkaz **Dock in parent container** . Tím se automaticky nastaví vlastnost PictureBox **Dock** na **Fill**. Chcete-li to vidět, zvolte ovládací prvek **PictureBox,** který chcete vybrat, přejděte do okna **Vlastnosti** a ujistěte se, že vlastnost **Dock** je nastavena na **Fill**.

1. Vytvořte PictureBox protápí oba sloupce změnou jeho **ColumnSpan** vlastnost. V **PictureBoxu**zvolte ovládací prvek **PictureBox** a nastavte jeho vlastnost **ColumnSpan** na **2**. Také když PictureBox je prázdný, chcete zobrazit prázdný rámeček. Nastavte vlastnost **BorderStyle** na **Fixed3D**.

    > [!NOTE]
    > Pokud nevidíte **ColumnSpan** vlastnost pro PictureBox, pak je pravděpodobné, že PictureBox byl přidán do formuláře, nikoli TableLayoutPanel. Chcete-li tento problém vyřešit, zvolte **PictureBox**, odstraňte jej, zvolte **TableLayoutPanel**a přidejte nový PictureBox.

1. Zvolte **panel TableLayoutPanel** ve formuláři a přidejte do formuláře ovládací prvek CheckBox. Poklepáním na položku **CheckBox** v **panelu nástrojů** přidejte nový ovládací prvek CheckBox do další volné buňky v tabulce. Vzhledem k tomu, že PictureBox zabírá první dvě buňky v TableLayoutPanel, checkbox ovládací prvek je přidán do levé dolní buňky. Zvolte vlastnost **Text** a zadejte do slova **Roztáhnout**, jak je znázorněno na následujícím obrázku.

    ![Ovládací prvek TextBox s vlastností Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>*Ovládací prvek* ***TextBox*** s *vlastností* ***Stretch***

1. Zvolte **TableLayoutPanel** ve formuláři a pak přejděte do **skupiny Kontejnery** v **panelu nástrojů** (kde jste dostali ovládací prvek TableLayoutPanel) a poklepáním na položku **FlowLayoutPanel** přidejte nový ovládací prvek do poslední buňky (vpravo dole). Potom ukotvit FlowLayoutPanel v TableLayoutPanel. Můžete tak učinit buď výběrem **Dock v nadřazeném kontejneru** v seznamu úkolů černého trojúhelníku FlowLayoutPanel, nebo nastavením vlastnosti **Dock** programu FlowLayoutPanel na **Fill**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> je kontejner, který uspořádá další ovládací prvky v řádku, jeden po druhém. Když změníte velikost FlowLayoutPanel, rozloží všechny jeho ovládací prvky v jednom řádku, pokud má prostor k tomu. V opačném případě je uspořádá v řádcích, jeden nad druhým. <br/><br/>Zde budete používat FlowLayoutPanel držet čtyři tlačítka. Pokud tlačítka uspořádat jeden na sebe při jejich přidání, ujistěte se, že vyberete FlowLayoutPanel před přidáním tlačítek. <br/><br/>(Každá buňka obvykle obsahuje pouze jeden ovládací prvek. V tomto příkladu obsahuje pravá dolní buňka tablelayoutpanel čtyři ovládací prvky tlačítek. Proč?  Protože FlowLayoutPanel je ovládací prvek kontejneru, což je ovládací prvek v buňce, která obsahuje další ovládací prvky.)

## <a name="to-add-buttons"></a>Přidání tlačítek

1. Zvolte nový FlowLayoutPanel, který jste přidali. Přejděte na **Společné ovládací prvky** v **panelu nástrojů** a poklepáním na položku **Button** přidejte do panelu FlowLayoutPanel ovládací prvek s názvem **button1.** Opakováním přidáte další tlačítko. IDE určuje, že již existuje tlačítko s názvem **button1** a volá další **tlačítko2**.

1. Ostatní tlačítka obvykle přidáte pomocí **panelu nástrojů**. Tentokrát zvolte **button2**a pak z řádku nabídek zvolte **Upravit** > **kopii** (nebo stiskněte **Ctrl**+**C**). Potom zvolte **Upravit** > **vložit** z řádku nabídek (nebo stiskněte **Ctrl**+**V)** a vložte kopii tlačítka. Nyní jej vložte znovu. Všimněte si, že rozhraní IDE přidá **button3** a **button4** flowlayoutpanel.

    > [!NOTE]
    > Můžete zkopírovat a vložit libovolný ovládací prvek. IDE názvy a umístí nové ovládací prvky logickým způsobem. Pokud vložíte ovládací prvek do kontejneru, ide zvolí další logický prostor pro umístění.

1. Zvolte první tlačítko a nastavte jeho vlastnost **Text** na **Zobrazit obrázek**. Potom nastavte vlastnosti **Text** dalších tří tlačítek na **vymazat obrázek**, **Nastavit barvu pozadí**a **Zavřít**.

1. Zvětšeme tlačítka a uspořádejte je tak, aby se zarovnaly na pravou stranu panelu. Zvolte **FlowLayoutPanel** a podívejte se na jeho **FlowDirection** vlastnost. Změňte ji tak, aby byla nastavena na **RightToLeft**.

   Tlačítka by se měla zarovnat k pravé straně buňky a obrátit jejich pořadí tak, aby bylo vpravo tlačítko **Zobrazit obrázek.**

    > [!NOTE]
    > Pokud jsou tlačítka stále v nesprávném pořadí, můžete přetáhnout tlačítka kolem FlowLayoutPanel změnit jejich uspořádání v libovolném pořadí. Můžete si vybrat tlačítko a přetáhnout ho doleva nebo doprava.

1. Vyberte tlačítko **Zavřít.** Chcete-li vybrat zbytek tlačítek současně, stiskněte a podržte klávesu **Ctrl** a vyberte je také.

   Po výběru všech tlačítek přejděte do okna **Vlastnosti** a posuňte se nahoru na vlastnost **AutoSize.** Tato vlastnost říká, že tlačítko automaticky změnit velikost sám tak, aby se vešly všechny jeho text. Nastavte ji na **hodnotu True**.

   Tlačítka by nyní měla být správně dimenzována a měla by být ve správném pořadí. (Dokud jsou vybrána všechna čtyři tlačítka, můžete změnit všechny čtyři vlastnosti **automatické velikosti** současně.) Na následujícím obrázku jsou zobrazena čtyři tlačítka.

    ![Prohlížeč obrázků se čtyřmi tlačítky](../ide/media/express_autosize.png)<br/>***Prohlížeč obrázků se*** *čtyřmi tlačítky*

1. Nyní spusťte program znovu, abyste viděli změny.

   Všimněte si, že tlačítka a zaškrtávací políčko ještě&mdash;nic nedělají, ale brzy ano.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

* Další krok kurzu najdete v **[tématu Krok 6: Pojmenování ovládacích prvků tlačítek](../ide/step-6-name-your-button-controls.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 4: Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
