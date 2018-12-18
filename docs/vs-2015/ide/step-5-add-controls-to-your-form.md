---
title: 'Krok 5: Přidejte do svého formuláře ovládací prvky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f7c65577a08b9aa9d6750b857e2c38939031f38
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257020"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Přidejte do svého formuláře ovládací prvky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku přidáte ovládací prvky, například `PictureBox` ovládacího prvku a `CheckBox` ovládací prvek do formuláře. Potom přidáte tlačítka do formuláře.  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 2](http://go.microsoft.com/fwlink/?LinkId=205200). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-add-controls-to-your-form"></a>Chcete-li přidat ovládací prvky do formuláře  
  
1.  Přejděte na kartu panelu nástrojů (umístěna na levé straně rozhraní IDE sady Visual Studio) a rozbalte **běžné ovládací prvky** skupiny. Zobrazí nejběžnější ovládací prvky, které vidíte ve formulářích.  
  
2.  Vyberte ovládací prvek TableLayoutPanel ve formuláři. Pokud chcete ověřit, že je vybrán kontejner TableLayoutPanel, ujistěte se, že jeho název zobrazuje v rozevíracím seznamu v horní části **vlastnosti** okna. Můžete také vybrat ovládací prvky formuláře pomocí rozevíracího seznamu v horní části **vlastnosti** okna. Výběr ovládacího prvku tímto způsobem může často být jednodušší než volba prvku tiny pomocí myši.  
  
3.  Dvakrát klikněte **PictureBox** položky pro přidání ovládacího prvku PictureBox do formuláře. Protože kontejner TableLayoutPanel je ukotven k vyplnění formuláře, rozhraní IDE přidá ovládací prvek PictureBox do první prázdné buňky (levý horní roh).  
  
4.  Zvolte nový ovládací prvek PictureBox vyberte ho a pak zvolte na černý trojúhelník na novém ovládacím prvku PictureBox k zobrazení jeho seznamu úloh, jak je znázorněno na následujícím obrázku.  
  
     ![Úlohy třídy PictureBox](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks")  
Úlohy třídy PictureBox  
  
    > [!NOTE]
    >  Pokud omylem přidáte nesprávný typ ovládacího prvku do vašeho kontejneru TableLayoutPanel, můžete ho odstranit. Klikněte pravým tlačítkem na ovládací prvek a klikněte na tlačítko **odstranit** v kontextové nabídce. Můžete také odebrat ovládací prvky z formuláře pomocí panelu nabídek. V panelu nabídky zvolte **upravit**, **zpět**, nebo **upravit**, **odstranit**.  
  
5.  Zvolte **ukotvit v nadřazeném kontejneru** odkaz. Tím se automaticky nastaví ovládací prvek PictureBox **Dock** vlastnost **vyplnit**. Tento údaj zobrazíte, zvolte ovládací prvek PictureBox vyberte ho, přejděte na **vlastnosti** okna, a ujistěte se, že **Dock** je nastavena na **vyplnit**.  
  
6.  Nechejte PictureBox roztáhnout oba sloupce změnou jeho **ColumnSpan** vlastnost. Vyberte ovládací prvek PictureBox a nastavte jeho **ColumnSpan** vlastnost **2**. Také když je PictureBox prázdný, budete chtít zobrazit prázdný rámeček. Nastavte jeho **BorderStyle** vlastnost **Fixed3D**.  
  
    > [!NOTE]
    >  Pokud se nezobrazí **ColumnSpan** vlastnost pro váš ovládací prvek PictureBox, pak je pravděpodobné, že ovládací prvek PictureBox byl přidán do formuláře, nikoli do TableLayoutPanel. Chcete-li tento problém vyřešit, zvolte ovládací prvek PictureBox, odstraňte ji, vyberte TableLayoutPanel a potom přidejte nový prvek PictureBox.  
  
7.  Vyberte TableLayoutPanel ve formuláři a potom přidat **zaškrtávací políčko** ovládacího prvku na formuláři. Dvakrát klikněte **zaškrtávací políčko** položky v panelu nástrojů a přidat nový ovládací prvek CheckBox do další volné buňky v tabulce. Protože PictureBox zabírá v kontejneru TableLayoutPanel první dvě buňky, ovládací prvek CheckBox je přidán do levé dolní buňky. Zvolte **Text** vlastnost a zadejte hledané klíčové slovo **Stretch**, jak je znázorněno na následujícím obrázku.  
  
     ![TextBox – ovládací prvek s vlastností Stretch](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox")  
TextBox – ovládací prvek s vlastností Stretch  
  
8.  Vyberte TableLayoutPanel ve formuláři a potom přejděte ke **kontejnery** skupině na panelu nástrojů (kde jste získali váš ovládací prvek) a dvakrát klikněte **FlowLayoutPanel** položky pro přidání nového ovládacího prvku do poslední buňky v ovládacím prvku PictureBox (vpravo dole). Potom ukotvěte FlowLayoutPanel v TableLayoutPanel (výběrem **ukotvit v nadřazeném kontejneru** v seznamu úloh černého trojúhelníku panelu FlowLayoutPanel nebo nastavením panelu FlowLayoutPanel **ukotvit** Vlastnost **vyplnit**).  
  
    > [!NOTE]
    >  FlowLayoutPanel je kontejner, který uspořádá jiné ovládací prvky do úhledných řádků v pořadí. Když změníte velikost FlowLayoutPanel, pokud má místo k rozložení všech ovládacích prvků v jediném řádku, udělá to. V opačném případě je uspořádá na řádcích, jednoho nad druhým. Použijete FlowLayoutPanel k podržení čtyř tlačítek. Pokud jsou tlačítka uspořádány, jeden v druhém při přidání, ujistěte se, že je vybraná FlowLayoutPanel před přidáním tlačítek. I když bylo uvedeno dříve, že každá buňka může obsahovat pouze jeden ovládací prvek, pravém dolním rohu buňky kontejneru TableLayoutPanel má čtyři ovládací prvky tlačítka. Je to proto, že do buňky obsahující další ovládací prvky můžete umístit ovládací prvek. Tento druh ovládacího prvku se nazývá kontejner a FlowLayoutPanel je kontejner.  
  
### <a name="to-add-buttons"></a>Přidat tlačítka  
  
1.  Vyberte nový FlowLayoutPanel, který jste přidali. Přejděte na **běžné ovládací prvky** v panelu nástrojů a dvojím kliknutím **tlačítko** položky pro přidání ovládacího tlačítka nazvaného **button1** do vašeho kontejneru FlowLayoutPanel. Opakujte k přidání dalšího tlačítka. Rozhraní IDE zjistí, že je již tlačítko nazvané **button1** a další nazve **button2**.  
  
2.  Obvykle přidáte další tlačítka pomocí panelu nástrojů. Tentokrát vyberte možnost **button2**a pak na panelu nabídek zvolte **upravit**, **kopírování** (nebo stiskněte kombinaci kláves Ctrl + C). V panelu nabídky zvolte **upravit**, **vložte** (nebo stiskněte klávesy Ctrl + V) k vložení kopie vašeho tlačítka. Nyní jej vložte znovu. IDE nyní přidalo **button3** a **button4** do FlowLayoutPanel.  
  
    > [!NOTE]
    >  Můžete zkopírovat a vložit libovolný ovládací prvek. Rozhraní IDE pojmenuje a umístí nové ovládací prvky logickým způsobem. Pokud vložíte ovládací prvek do kontejneru, rozhraní IDE zvolí další logický prostor pro umístění.  
  
3.  Vyberte první tlačítko a nastavte jeho **Text** vlastnost **zobrazit obrázek**. Nastavte **Text** vlastnosti dalších tří tlačítek na **Vymazat obrázek**, **nastavit barvu pozadí**, a **Zavřít**.  
  
4.  Dalším krokem je změnit velikost tlačítek a uspořádat je tak, aby jejich zarovnání bylo k pravé straně panelu. Vyberte FlowLayoutPanel a podívejte se na jeho **FlowDirection** vlastnost. Změňte ji tak, že je nastavena na **RightToLeft**. Jakmile provedete, tlačítka by měl vlastní vyrovnání v rámci na pravou stranu buňky a jejich pořadí se obrátit tak, aby **zobrazit obrázek** je tlačítko na pravé straně.  
  
    > [!NOTE]
    >  Pokud jsou tlačítka stále v nesprávném pořadí, můžete přetáhnout tlačítka kolem kontejneru FlowLayoutPanel k změně jejich uspořádání v libovolném pořadí. Můžete zvolit tlačítko a přetáhnout je doleva nebo doprava.  
  
5.  Zvolte **Zavřít** tlačítko a vyberte ji. Podržte stisknutou klávesu CTRL a vyberte další tři tlačítka tak, aby byly všechny vybrány. Zatímco jsou všechna tlačítka vybrána, přejděte **vlastnosti** okno a posouvejte nahoru až **AutoSize** vlastnost. Tato vlastnost říká tlačítku, že automaticky změní velikost sebe sama na vhodnou všechen text. Nastavte ho na **true**. Tlačítka by měla být nyní správně velká a být ve správném pořadí. (Dokud jsou vybrány všechna čtyři tlačítka, můžete změnit všechny čtyři **AutoSize** vlastnosti ve stejnou dobu.) Následující obrázek znázorňuje čtyři tlačítka.  
  
     ![Prohlížeč obrázků se čtyřmi tlačítky](../ide/media/express-autosize.png "Express_AutoSize")  
Prohlížeč obrázků se čtyřmi tlačítky  
  
6.  Nyní spusťte váš program znovu, abyste viděli váš nově rozložený formulář. Volba tlačítek a zaškrtávacího políčka ještě nic neumí, ale bude brzy fungovat.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 6: název vašeho ovládací prvky tlačítka](../ide/step-6-name-your-button-controls.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 4: rozložení na svůj formulář pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).



