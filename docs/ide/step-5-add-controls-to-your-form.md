---
title: 'Krok 5: Přidejte do svého formuláře ovládací prvky'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7a0167d4d5af125e706350002ccf8a17e459414
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748553"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Přidejte do svého formuláře ovládací prvky
V tomto kroku přidáte ovládací prvky, jako například <xref:System.Windows.Forms.PictureBox> řízení a <xref:System.Windows.Forms.CheckBox> do svého formuláře ovládací prvek. Potom přidáte <xref:System.Windows.Forms.Button> ovládacích prvků do svého formuláře.

 ![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v části [kurzu 1: vytvoření prohlížeče obrázků v jazyce Visual Basic – Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) nebo [kurzu 1: vytvoření prohlížeče obrázků v jazyce C# - Video 2](http://go.microsoft.com/fwlink/?LinkId=205200). Tyto videa pomocí starší verze sady Visual Studio, takže drobné rozdíly v některé příkazy a další prvky uživatelského rozhraní. Však koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

## <a name="to-add-controls-to-your-form"></a>K přidávání ovládacích prvků do svého formuláře

1.  Přejděte na **sada nástrojů** karta (nachází se na levé straně Visual Studio IDE) a rozbalte **běžné ovládací prvky** skupiny. Ukazuje to nejběžnější ovládací prvky se zobrazí ve formulářích.

2.  Vyberte **TableLayoutPanel** ovládací prvek na formuláři. Pokud chcete ověřit, že je vybraný kontejner TableLayoutPanel, ujistěte se, že její název se zobrazí v rozevíracím seznamu v horní části **vlastnosti** okno. Můžete také ovládacích prvků formuláře pomocí rozevíracího seznamu v horní části **vlastnosti** okno. Výběr ovládacího prvku tímto způsobem může být často jednodušší než výběr prvku jen nepatrnou pomocí myši.

3.  Dvakrát klikněte **PictureBox** položky ovládacího prvku PictureBox přidáte do svého formuláře. Protože kontejner TableLayoutPanel je ukotven k vyplnění formuláře, rozhraní IDE přidá ovládacího prvku PictureBox první prázdné buňky (levém horním rohu).

4.  Zvolte nový **PictureBox** řízení ji vyberte a potom zvolte černý trojúhelník na novém ovládacím prvku PictureBox zobrazíte jeho seznamu úloh, jak je znázorněno na následujícím obrázku.

     ![PictureBox úlohy](../ide/media/express_pictureboxtasks.png)
**PictureBox** úlohy

    > [!NOTE]
    >  Pokud omylem přidáte nesprávný typ ovládacího prvku do vaší TableLayoutPanel, můžete ji odstranit. Klikněte pravým tlačítkem na ovládací prvek a potom vyberte **odstranit** v jeho místní nabídce. Ovládací prvky můžete také odebrat z formuláře pomocí panelu nabídek. Na řádku nabídek zvolte **upravit** > **vrátit zpět**, nebo **upravit** > **odstranit**.

5.  Vyberte **ukotvení v nadřazený kontejner** odkaz. Tím se automaticky nastaví PictureBox **ukotvení** vlastnost **vyplnění**. To zobrazit, vyberte **PictureBox** vyberte ovládací prvek, přejděte na **vlastnosti** okno, a ujistěte se, že **ukotvení** je nastavena na **vyplnění**.

6.  Ujistěte se, PictureBox roztáhnout oba sloupce změnou jeho **ColumnSpan** vlastnost. Vyberte **PictureBox** řízení a nastavit jeho **ColumnSpan** vlastnost **2**. Navíc pokud PictureBox prázdné, budete chtít zobrazit prázdný rámeček. Nastavte její **styl okraje** vlastnost **Fixed3D**.

    > [!NOTE]
    >  Pokud se nezobrazí **ColumnSpan** vlastnost pro vaše PictureBox a pak je pravděpodobné, že PictureBox byl přidán do formuláře, nikoli TableLayoutPanel. Chcete-li odstranit tento problém, zvolte **PictureBox**, odstranit, vyberte **TableLayoutPanel**, a pak přidejte nový PictureBox.

7.  Vyberte **TableLayoutPanel** na formuláři a poté přidejte ovládací prvek zaškrtávací políčko pro formulář. Dvakrát klikněte **zaškrtávací políčko** položky v **sada nástrojů** přidat nový ovládací prvek CheckBox další volné buňku v tabulce. Protože PictureBox zabírá první dvě buňky v kontejneru TableLayoutPanel, ovládací prvek zaškrtávací políčko se přidá do levého dolního buňky. Vyberte **Text** vlastností a zadejte slovo **Stretch**, jak je znázorněno na následujícím obrázku.

     ![TextBox – ovládací prvek s vlastností Stretch](../ide/media/express_pictureviewercheckbox.png)
**TextBox** řízení s **Stretch** vlastnost

8.  Vyberte **TableLayoutPanel** na formulář a potom přejděte na **kontejnery** v **sada nástrojů** (které jste získali vaše TableLayoutPanel – ovládací prvek) a dvakrát klikněte na **FlowLayoutPanel** položky k přidání nového ovládacího prvku na poslední buňky v ovládacím prvku PictureBox (vpravo dole). Potom ukotvení FlowLayoutPanel v kontejneru TableLayoutPanel (buď výběrem **ukotvení v nadřazený kontejner** na seznam úkolů černý trojúhelník FlowLayoutPanel nebo nastavením FlowLayoutPanel **ukotvení** Vlastnost **vyplnění**).

    > [!NOTE]
    >  A <xref:System.Windows.Forms.FlowLayoutPanel> je kontejner, který uspořádá dalších ovládacích prvků v úhledné řádků v pořadí. Při změně velikosti ovládacího prvku FlowLayoutPanel, pokud má místo pro vzhled všech ovládacích prvků do jednoho řádku, udělá to. Jinak je uspořádá na řádky, jeden na druhý. FlowLayoutPanel použije k uložení čtyři tlačítka. Pokud tlačítka uspořádat jednu na jiné při přidání top, ujistěte se, že je vybraný FlowLayoutPanel před přidáním tlačítka. I když bylo uvedeno dříve, každá buňka může obsahovat pouze jeden prvek, na pravém buňku kontejneru TableLayoutPanel má čtyři ovládací prvky tlačítek. Je to proto, že můžete vložit ovládací prvek v buňce, který obsahuje další ovládací prvky. Tento druh ovládacího prvku se nazývá kontejner a FlowLayoutPanel je kontejner.

## <a name="to-add-buttons"></a>Přidání tlačítek

1.  Zvolte nové FlowLayoutPanel, který jste přidali. Přejděte na **běžné ovládací prvky** v **sada nástrojů** a dvakrát klikněte na **tlačítko** položka k přidání ovládacího prvku tlačítko názvem **button1** k vaší FlowLayoutPanel. Opakujte jiné tlačítko Přidat. Rozhraní IDE zjistí, že již tlačítka nazvaného **button1** a volá dalšímu **button2**.

2.  Obvykle přidávat další tlačítka pomocí **sada nástrojů**. Tentokrát vyberte **button2**a potom na panelu nabídek vyberte **upravit** > **kopie** (nebo stiskněte klávesu **Ctrl** + **C**). Na řádku nabídek zvolte **upravit** > **vložit** (nebo stiskněte klávesu **Ctrl**+**V**) k vložení kopie vašeho tlačítka. Nyní vložte znovu. Prostředí IDE nyní přidala **button3** a **button4** k FlowLayoutPanel.

    > [!NOTE]
    >  Můžete zkopírovat a vložit libovolný ovládací prvek. Prostředí IDE názvy a umístí nové ovládací prvky logickým způsobem. Pokud můžete vložit ovládacího prvku do kontejneru, rozhraní IDE zvolí další logický místa pro umístění.

3.  Zvolte tlačítko první a nastavit jeho **Text** vlastnost **zobrazit obrázek**. Nastavte **Text** vlastnosti následující tři tlačítka na **Vymazat obrázek**, **nastavení barvy pozadí**, a **Zavřít**.

4.  Dalším krokem je velikost tlačítek a uspořádat je tak, aby se na pravé straně panelu zarovnané. Vyberte **FlowLayoutPanel** a prohlédněte si jeho **FlowDirection** vlastnost. Ho změnit tak, že nastavíte **RightToLeft**. Jakmile to uděláte, doporučujeme tlačítka vlastní vyrovnání u pravého okraje buňky a změnit jejich pořadí tak, aby **zobrazit obrázek** tlačítko je na pravé straně.

    > [!NOTE]
    >  Pokud tlačítka jsou stále v nesprávném pořadí, můžete přetáhnout tlačítka kolem FlowLayoutPanel ke změně uspořádání je v libovolném pořadí. Můžete vybrat tlačítko a přetáhněte jej doleva nebo doprava.

5.  Vyberte **Zavřít** tlačítko ji vyberte. Podržte stisknutou **Ctrl** klíče a zvolte další tři tlačítka, tak, aby byly všechny vybrány. Když jsou vybrány všechny tlačítka, přejděte na **vlastnosti** okno a přejděte do **AutoSize** vlastnost. Tato vlastnost určuje, na tlačítko automaticky měnit velikost tak, aby vyhovovaly všechen text. Nastavte ji na **true**. Vaše tlačítka by měl být nyní správně velká a být ve správném pořadí. (Tak dlouho, dokud jsou vybrány všechny čtyři tlačítka, můžete změnit všechny čtyři **AutoSize** vlastnosti ve stejnou dobu.) Následující obrázek znázorňuje čtyři tlačítka.

     ![Obrázek prohlížeč s čtyři tlačítka](../ide/media/express_autosize.png)
**Prohlížeč obrázků** s čtyři tlačítka

6.  Nyní spusťte program znovu zobrazíte nově rozložený formulář. Výběr tlačítka a zaškrtávací políčko ještě nic neudělá, ale bude brzy fungovat.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 6: pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 4: Rozvrhněte svůj formulář pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
