---
title: 'Krok 5: Přidejte ovládací prvky do formuláře | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6e66c8192b1fa409482bd33287cec04f74c1304
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851533"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Přidejte do svého formuláře ovládací prvky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku přidáte ovládací prvky, například ovládací prvek `PictureBox` a ovládací prvek `CheckBox`, do formuláře. Pak přidáte tlačítka do formuláře.

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-video 2](https://msdn.microsoft.com/vbasic/gg315945.aspx) nebo v [kurzu 1: vytvoření prohlížeče obrázků ve C# videu 2](https://msdn.microsoft.com/vcsharp/gg278410.aspx). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-add-controls-to-your-form"></a>Přidání ovládacích prvků do formuláře

1. Přejít na kartu panel nástrojů (umístěný na levé straně integrovaného vývojového prostředí sady Visual Studio) a rozbalte skupinu **běžné ovládací prvky** . Tím se zobrazí nejběžnější ovládací prvky, které vidíte ve formulářích.

2. Vyberte ovládací prvek TableLayoutPanel ve formuláři. Chcete-li ověřit, zda je kontejner TableLayoutPanel vybrán, ujistěte se, že se jeho název zobrazuje v rozevíracím seznamu v horní části okna **vlastnosti** . Pomocí rozevíracího seznamu v horní části okna **vlastnosti** můžete také zvolit ovládací prvky formuláře. Výběr ovládacího prvku tímto způsobem může být často snazší než volba nemalého ovládacího prvku pomocí myši.

3. Dvojím kliknutím na položku **PictureBox** přidáte ovládací prvek PictureBox do formuláře. Vzhledem k tomu, že kontejner TableLayoutPanel je ukotven pro vyplnění formuláře, rozhraní IDE přidá ovládací prvek PictureBox do první prázdné buňky (levý horní roh).

4. Zvolte nový ovládací prvek PictureBox, který chcete vybrat, a pak zvolte černý trojúhelník na novém ovládacím prvku PictureBox pro zobrazení seznamu úkolů, jak je znázorněno na následujícím obrázku.

     ![Úlohy PictureBox](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks") Úlohy PictureBox

    > [!NOTE]
    > Pokud omylem přidáte nesprávný typ ovládacího prvku do kontejneru TableLayoutPanel, můžete jej odstranit. Klikněte na ovládací prvek pravým tlačítkem myši a potom v místní nabídce vyberte možnost **Odstranit** . Ovládací prvky můžete odebrat také z formuláře pomocí panelu nabídek. Na řádku nabídek klikněte na položku **Upravit**, **zpět**nebo **Upravit**, **Odstranit**.

5. Vyberte odkaz **Dock v nadřazeném kontejneru** . Tím se automaticky nastaví vlastnost PictureBox **Dock** na **Fill**. Chcete-li se podívat, zvolte ovládací prvek PictureBox, který chcete vybrat, přejděte do okna **vlastnosti** a ujistěte se, že vlastnost **Dock** je nastavena na hodnotu **Fill**.

6. Nastavte, aby PictureBox rozspan oba sloupce změnou jeho vlastnosti **jeho ColumnSpan** . Vyberte ovládací prvek PictureBox a nastavte jeho vlastnost **jeho ColumnSpan** na hodnotu **2**. Také, pokud je PictureBox prázdné, chcete zobrazit prázdný rámeček. Nastavte jeho vlastnost **BorderStyle** na **Fixed3D**.

    > [!NOTE]
    > Pokud nevidíte vlastnost **jeho ColumnSpan** ovládacího prvku PictureBox, je možné, že byl ovládací prvek PictureBox přidán do formuláře namísto kontejneru TableLayoutPanel. Chcete-li tento problém opravit, zvolte PictureBox, odstraňte jej, zvolte kontejner TableLayoutPanel a pak přidejte nový PictureBox.

7. Zvolte kontejner TableLayoutPanel ve formuláři a poté přidejte ovládací prvek **CheckBox** do formuláře. Dvojitým kliknutím na položku **CheckBox** v sadě nástrojů přidáte nový ovládací prvek CheckBox do další volné buňky v tabulce. Vzhledem k tomu, že PictureBox zabírá první dvě buňky v kontejneru TableLayoutPanel, ovládací prvek CheckBox se přidá do levé dolní buňky. Vyberte vlastnost **text** a zadejte slovo **roztáhnout**, jak je znázorněno na následujícím obrázku.

     ![Ovládací prvek TextBox s vlastností Stretch](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox") Ovládací prvek TextBox s vlastností Stretch

8. Zvolte kontejner TableLayoutPanel ve formuláři a potom přejděte do skupiny **kontejnery** v sadě nástrojů (kde jste získali svůj ovládací prvek TableLayoutPanel) a dvakrát klikněte na položku **FlowLayoutPanel** a přidejte nový ovládací prvek do poslední buňky v ovládacím prvku PictureBox (vpravo dole). Poté ukotvěte FlowLayoutPanel v kontejneru TableLayoutPanel (buď výběrem možnosti **Dock v nadřazeném kontejneru** v seznamu úkolů černého trojúhelníku FlowLayoutPanel, nebo nastavením vlastnosti **Dock** prvku FlowLayoutPanel na **vyplnit**).

    > [!NOTE]
    > FlowLayoutPanel je kontejner, který uspořádá další ovládací prvky v úhledných řádcích v daném pořadí. Když změníte velikost kontejneru FlowLayoutPanel, pokud má místo pro rozložení všech ovládacích prvků na jednom řádku, provede to. V opačném případě je uspořádá na řádcích, jeden nad druhou. K uložení čtyř tlačítek použijete FlowLayoutPanel. Pokud jsou tlačítka při přidání uspořádána po sobě, před přidáním tlačítek se ujistěte, že je vybráno FlowLayoutPanel. Ačkoliv bylo uvedeno dříve, že každá buňka může obsahovat pouze jeden ovládací prvek, pravá dolní buňka kontejneru TableLayoutPanel má čtyři ovládací prvky tlačítka. Důvodem je to, že ovládací prvek lze umístit do buňky, která obsahuje jiné ovládací prvky. Tento druh ovládacího prvku se nazývá kontejner a FlowLayoutPanel je kontejner.

### <a name="to-add-buttons"></a>Přidání tlačítek

1. Vyberte nový FlowLayoutPanel, který jste přidali. Přejděte na **běžné ovládací prvky** v sadě nástrojů a dvojitým kliknutím na položku **tlačítka** přidejte ovládací prvek tlačítko s názvem **Button1** do kontejneru FlowLayoutPanel. Opakováním přidejte další tlačítko. Rozhraní IDE zjistí, že již existuje tlačítko s názvem **Button1** a volá další **Button2**.

2. Obvykle přidáte další tlačítka pomocí sady nástrojů. Tentokrát zvolte možnost **Button2**a pak na panelu nabídek zvolte možnost **Upravit**, **Kopírovat** (nebo stiskněte klávesovou zkratku CTRL + C). Na panelu nabídek zvolte možnost **Upravit**, **Vložit** (nebo stiskněte klávesovou zkratku CTRL + V) a vložte kopii tlačítka. Nyní jej vložte znovu. Integrované vývojové prostředí (IDE) teď přidalo **Button3** a **Button4** do kontejneru FlowLayoutPanel.

    > [!NOTE]
    > Můžete zkopírovat a vložit libovolný ovládací prvek. Rozhraní IDE názvy a umístí nové ovládací prvky logickým způsobem. Pokud ovládací prvek vložíte do kontejneru, rozhraní IDE zvolí další logický prostor pro umístění.

3. Vyberte první tlačítko a nastavte jeho vlastnost **text** tak, aby **zobrazovala obrázek**. Potom nastavte vlastnosti **textu** dalších tří tlačítek pro **vymazání obrázku**, **Nastavení barvy pozadí**a **zavření**.

4. Dalším krokem je změnit velikost tlačítek a uspořádat je tak, aby se zarovnaly na pravé straně panelu. Vyberte FlowLayoutPanel a podívejte se na jeho vlastnost **FlowDirection** . Změňte ji tak, aby byla nastavená na **RightToLeft**. Jakmile to uděláte, tlačítka by se měla zarovnat do pravé strany buňky a obrátit jejich pořadí tak, aby tlačítko **Zobrazit obrázek** bylo na pravé straně.

    > [!NOTE]
    > Pokud jsou tlačítka stále v nesprávném pořadí, můžete přetáhnout tlačítka kolem FlowLayoutPanel a změnit jejich uspořádání v libovolném pořadí. Můžete zvolit tlačítko a přetáhnout ho doleva nebo doprava.

5. Kliknutím na tlačítko **Zavřít** jej vyberte. Podržte stisknutou klávesu CTRL a vyberte další tři tlačítka, aby byly všechny vybrány. Když jsou vybrána všechna tlačítka, přejděte do okna **vlastnosti** a posuňte se k vlastnosti **AutoSize** . Tato vlastnost oznamuje tlačítku, aby se automaticky změnila velikost tak, aby odpovídala veškerému jeho textu. Nastavte na **hodnotu true**. Tlačítka by měla být teď správně velikostná a musí být ve správném pořadí. (Pokud jsou vybrána všechna čtyři tlačítka, můžete změnit všechny čtyři vlastnosti **AutoSize** současně.) Následující obrázek znázorňuje čtyři tlačítka.

     ![Prohlížeč obrázků se čtyřmi tlačítky](../ide/media/express-autosize.png "Express_AutoSize") Prohlížeč obrázků se čtyřmi tlačítky

6. Nyní spusťte program znovu, aby se zobrazila vaše nově rozložená forma. Výběr tlačítek a zaškrtávací políčko ještě nic nedělá, ale bude brzy fungovat.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přejděte na [Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
