---
title: Vytvoření webové části pro službu SharePoint pomocí návrháře
description: V tomto návodu vytvoříte vizuální webovou část pomocí šablony projektu Visual Web Part na SharePointu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 02a0eb7c9279aef1fd2821d44a6f3cc4a0008356
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847749"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře

Pokud vytvoříte webové části pro web služby SharePoint, uživatelé mohou přímo upravit obsah, vzhled a chování stránek v dané lokalitě pomocí prohlížeče. V tomto návodu se dozvíte, jak vizuálně vytvořit webovou část pomocí šablony projektu **vizuální webové části** služby SharePoint v aplikaci Visual Studio.

Webová část, kterou vytvoříte, zobrazí měsíční zobrazení kalendáře a zaškrtávací políčko pro každý seznam kalendáře na webu. Zaškrtnutím políček můžou uživatelé určit, které seznamy kalendáře se mají zahrnout do zobrazení měsíčního kalendáře.

Tento návod znázorňuje následující úlohy:

- Vytvoření webové části pomocí šablony projektu **vizuální webové části** .
- Návrh webové části pomocí návrháře aplikace Visual Web Developer v aplikaci Visual Studio.
- Přidání kódu pro zpracování událostí ovládacích prvků ve webové části.
- Testování webové části ve službě SharePoint.

    > [!NOTE]
    > Váš počítač může v následujících pokynech zobrazit jiné názvy nebo umístění pro některé prvky uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

## <a name="create-a-web-part-project"></a>Vytvoření projektu webové části

Nejprve vytvořte projekt webové části pomocí šablony projektu **Visual Web Part** .

1. Spusťte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí možnosti **Spustit jako správce** .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

     Zobrazí se dialogové okno **Nový projekt**.

3. V dialogovém okně **Nový projekt** v části **Visual C#** nebo **Visual Basic** rozbalte možnost **Office/SharePoint** a pak zvolte kategorii **řešení SharePoint** .

4. V seznamu šablon vyberte šablonu **SharePoint 2013 – Visual Web Part** a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** . Pomocí tohoto průvodce můžete určit web, který budete používat k ladění projektu a úroveň důvěryhodnosti řešení.

5. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** vyberte možnost **nasadit jako řešení farmy** .

6. Kliknutím na tlačítko **Dokončit** přijměte výchozí místní web služby SharePoint.

## <a name="designing-the-web-part"></a>Návrh webové části

Navrhněte webovou část přidáním ovládacích prvků ze **sady nástrojů** na plochu návrháře aplikace Visual Web Developer.

1. V návrháři aplikace Visual Web Developer vyberte kartu **Návrh** a přepněte na zobrazení Návrh.

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **sadu nástrojů**.

3. V uzlu **standardní** na **panelu nástrojů** zvolte ovládací prvek **CheckBoxList** a pak proveďte jeden z následujících kroků:

    - Otevřete místní nabídku ovládacího prvku **CheckBoxList** , zvolte možnost **Kopírovat**, otevřete místní nabídku pro první řádek v návrháři a pak zvolte možnost **Vložit**.

    - Přetáhněte ovládací prvek **CheckBoxList** ze **sady nástrojů** a připojte ovládací prvek k prvnímu řádku v návrháři.

4. Opakujte předchozí krok, ale přesuňte tlačítko na další řádek návrháře.

5. V návrháři klikněte na tlačítko **Button1** .

6. Na panelu nabídek vyberte možnost **Zobrazit**  >  **okno vlastností**.

     Otevře se okno **vlastnosti** .

7. Do vlastnosti **text** tlačítka zadejte **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Zpracování událostí ovládacích prvků ve webové části

Přidejte kód, který umožňuje uživateli přidat kalendáře do zobrazení hlavního kalendáře.

1. Proveďte jednu z následujících sad kroků:

   - V Návrháři dvakrát klikněte na tlačítko **aktualizovat** .

   - V okně **vlastnosti** pro tlačítko **aktualizovat** klikněte na tlačítko **události** . Ve vlastnosti **Click** zadejte **Button1_Click** a pak zvolte klávesu ENTER.

     V editoru kódu se otevře soubor kódu uživatelského ovládacího prvku a `Button1_Click` zobrazí se obslužná rutina události. Později přidáte kód do této obslužné rutiny události.

2. Přidejte následující příkazy do horní části souboru kódu uživatelského ovládacího prvku.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Do třídy přidejte následující řádek kódu `VisualWebPart1` . Tento kód deklaruje ovládací prvek měsíčního zobrazení kalendáře.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Nahraďte `Page_Load` metodu `VisualWebPart1` třídy následujícím kódem. Tento kód provádí následující úlohy:

   - Přidá zobrazení měsíčního kalendáře do uživatelského ovládacího prvku.

   - Přidá zaškrtávací políčko pro každý seznam kalendáře na webu.

   - Určuje šablonu pro každý typ položky, která se zobrazí v zobrazení kalendáře.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Nahraďte `Button1_Click` metodu `VisualWebPart1` třídy následujícím kódem. Tento kód přidá položky z každého vybraného kalendáře do zobrazení hlavního kalendáře.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testování webové části

Při spuštění projektu se otevře web služby SharePoint. Webová část je automaticky přidána do galerie webových částí v SharePointu. K otestování tohoto projektu budete provádět následující úlohy:

- Přidejte událost do každého ze dvou samostatných seznamů kalendáře.
- Přidejte webovou část na stránku webové části.
- Zadejte seznamy, které se mají zahrnout do zobrazení měsíčního kalendáře.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Přidání událostí do seznamů kalendáře na webu

1. V aplikaci Visual Studio klikněte na klávesu **F5** .

     Otevře se web služby SharePoint a na [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] stránce se zobrazí panel Snadné spuštění.

2. Na panelu Snadné spuštění v části **seznamy** vyberte odkaz **Kalendář** .

     Zobrazí se stránka **Kalendář** .

     Pokud se žádný odkaz na kalendář nezobrazuje na panelu snadného spuštění, vyberte odkaz **obsah webu** . Pokud stránka s obsahem webu nezobrazuje položku **kalendáře** , vytvořte ji.

3. Na stránce kalendář zvolte den a pak kliknutím na odkaz **Přidat** ve vybraném dni přidejte událost.

4. Do pole **název** zadejte **událost ve výchozím kalendáři** a pak klikněte na tlačítko **Uložit** .

5. Zvolte odkaz **obsah webu** a pak zvolte dlaždici **Přidat aplikaci** .

6. Na stránce **vytvořit** vyberte typ **kalendáře** , pojmenujte kalendář a pak klikněte na tlačítko **vytvořit** .

7. Přidejte událost do nového kalendáře, pojmenujte událost události **ve vlastním kalendáři** a pak klikněte na tlačítko **Uložit** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Přidání webové části na stránku webové části

1. Na stránce **obsah webu** otevřete složku **stránky webu** .

2. Na pásu karet klikněte na kartu **soubory** , otevřete nabídku **Nový dokument** a zvolte příkaz **Stránka webové části** .

3. Na stránce **Nová stránka webové části** pojmenujte stránku **SampleWebPartPage. aspx** a klikněte na tlačítko **vytvořit** .

     Zobrazí se stránka webová část.

4. V horní zóně stránky webové části klikněte na kartu **Vložit** a potom klikněte na tlačítko **Webová část** .

5. Zvolte **vlastní** složku, zvolte webovou část **VisualWebPart1** a pak klikněte na tlačítko **Přidat** .

     Webová část se zobrazí na stránce. Ve webové části se zobrazí následující ovládací prvky:

    - Měsíční zobrazení kalendáře.

    - Tlačítko **aktualizovat**

    - Pole **Kalendář** .

    - Zaškrtávací políčko **vlastní kalendář** .

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Určení seznamů, které se mají zahrnout do zobrazení měsíčního kalendáře

Ve webové části zadejte kalendáře, které chcete zahrnout do zobrazení měsíčního kalendáře, a pak klikněte na tlačítko **aktualizovat** .

Události ze všech kalendářů, které jste zadali, se zobrazí v zobrazení měsíčního kalendáře.

## <a name="see-also"></a>Viz také

[Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Postupy: Vytvoření webové části](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 služby SharePoint [Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
