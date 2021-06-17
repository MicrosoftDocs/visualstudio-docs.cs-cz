---
title: Vytvoření webové části pro SharePoint pomocí návrháře
description: V tomto názorném postupu vytvoříte webovou část vizuálně pomocí šablony projektu webové části vizuálu služby SharePoint v Visual Studio.
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
ms.openlocfilehash: 55f69875b06428c9bbe179e73dd6ea9b4ef40b8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112454"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Návod: Vytvoření webové části pro SharePoint pomocí návrháře

Pokud vytváříte webové části pro sharepointový web, mohou uživatelé přímo upravovat obsah, vzhled a chování stránek na tomto webu pomocí prohlížeče. Tento názorný postup vám ukáže, jak vizuálně vytvořit webovou část pomocí šablony projektu webové části vizuálu **SharePointu** v Visual Studio.

Webová část, kterou vytvoříte, zobrazí zobrazení měsíčního kalendáře a zaškrtávací políčko pro každý seznam kalendáře na webu. Zaškrtnutím políček mohou uživatelé určit, které seznamy kalendářů se mají zahrnout do zobrazení měsíčního kalendáře.

Tento návod znázorňuje následující úlohy:

- Vytvoření webové části pomocí šablony **projektu webové části** vizuálu
- Návrh webové části pomocí návrháře Visual Web Developer v Visual Studio.
- Přidání kódu pro zpracování událostí ovládacích prvků ve webové části
- Testování webové části v SharePointu

    > [!NOTE]
    > Váš počítač může zobrazovat různé názvy nebo umístění některých prvků uživatelského rozhraní pro Visual Studio v následujících pokynech. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení integrovaného vývojového Visual Studio ide.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

## <a name="create-a-web-part-project"></a>Vytvoření projektu webové části

Nejprve vytvořte projekt webové části pomocí šablony projektu **webové části** vizuálu.

1. Začněte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] použitím možnosti Spustit **jako** správce.

2. Na řádku nabídek zvolte File New Project **(Soubor**  >  **nový**  >  **projekt).**
::: moniker range="=vs-2017"

3. V dialogovém **okně Nový** projekt v části **Visual C#** **nebo Visual Basic** rozbalte **Office/SharePoint** a pak zvolte kategorii **Řešení služby SharePoint.**

4. V seznamu šablon zvolte šablonu **SharePoint 2013 – Webová** část vizuálu a pak zvolte **tlačítko OK.**

     Zobrazí **se Průvodce přizpůsobením SharePointu.** Pomocí tohoto průvodce můžete určit web, který budete používat k ladění projektu, a úroveň důvěryhodnosti řešení.
::: moniker-end
::: moniker range=">=vs-2019"
3. V dialogovém **okně Vytvořit nový projekt** vyberte prázdný projekt *SharePointu** pro konkrétní verzi SharePointu, kterou jste nainstalovali. Pokud máte například instalaci SharePointu 2019, vyberte šablonu **SharePoint 2019 – prázdný** projekt.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. Do **pole Název** zadejte **TestProject1** a pak zvolte **tlačítko** Vytvořit.

::: moniker-end
5. V části **Jaká je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** zvolte tlačítko nasadit **jako řešení** farmy.

6. Zvolte tlačítko **Dokončit** a přijměte výchozí místní sharepointový web.

## <a name="designing-the-web-part"></a>Návrh webové části

Navrhovat webovou část přidáním ovládacích prvků z **panelu** nástrojů na plochu návrháře visual web developer.

1. V návrháři visual web developer zvolte kartu **Návrh** a přepněte na zobrazení Návrh.

2. V řádku nabídek zvolte Zobrazit **panel**  >  **nástrojů.**

3. V **uzlu Standard** panelu **nástrojů** zvolte ovládací prvek **CheckBoxList** a pak proveďte jeden z následujících kroků:

    - Otevřete místní nabídku pro ovládací prvek **CheckBoxList,** zvolte **Kopírovat,** otevřete místní nabídku pro první řádek v návrháři a pak zvolte **Vložit**.

    - Přetáhněte **ovládací prvek CheckBoxList** z **panelu nástrojů** a připojte ho k prvnímu řádku v návrháři.

4. Opakujte předchozí krok, ale přesuňte tlačítko na další řádek návrháře.

5. V návrháři zvolte **tlačítko Button1.**

6. V řádku nabídek zvolte **Zobrazit**  >  **okno Vlastnosti.**

     Otevře **se okno** Vlastnosti.

7. Do **vlastnosti Text** tlačítka zadejte **Aktualizovat**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Zpracování událostí ovládacích prvků ve webové části

Přidejte kód, který uživateli umožní přidat kalendáře do zobrazení hlavního kalendáře.

1. Proveďte jednu z následujících sad kroků:

   - V návrháři poklikejte na **tlačítko** Aktualizovat.

   - V **okně Vlastnosti** tlačítka **Aktualizovat** zvolte **tlačítko** Události. Do vlastnosti **Click** zadejte **Button1_Click** a pak stiskněte klávesu Enter.

     Soubor kódu uživatelského ovládacího prvku se otevře v Editoru kódu a zobrazí `Button1_Click` se obslužná rutina události. Později do této obslužné rutiny události přidáte kód.

2. Na začátek souboru kódu uživatelského ovládacího prvku přidejte následující příkazy.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Do třídy přidejte následující `VisualWebPart1` řádek kódu. Tento kód deklaruje ovládací prvek měsíčního zobrazení kalendáře.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. Nahraďte `Page_Load` metodu `VisualWebPart1` třídy následujícím kódem. Tento kód provádí následující úlohy:

   - Přidá do uživatelského ovládacího prvku zobrazení měsíčního kalendáře.

   - Přidá zaškrtávací políčko pro každý seznam kalendáře v lokalitě.

   - Určuje šablonu pro každý typ položky, který se zobrazí v zobrazení kalendáře.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. Nahraďte `Button1_Click` metodu `VisualWebPart1` třídy následujícím kódem. Tento kód přidá položky z každého vybraného kalendáře do zobrazení hlavního kalendáře.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Testování webové části

Při spuštění projektu se otevře sharepointový web. Webová část se automaticky přidá do Galerie webových částí v SharePointu. Pokud chcete tento projekt otestovat, provedete následující úlohy:

- Přidejte událost do každého ze dvou samostatných seznamů kalendáře.
- Přidejte webovou část na stránku webové části.
- Zadejte seznamy, které se mají zahrnout do zobrazení měsíčního kalendáře.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Přidání událostí do seznamů kalendáře na webu

1. V Visual Studio vyberte klávesu **F5.**

     Otevře se sharepointový web [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a Snadné spuštění se na stránce zobrazí panel pro správu.

2. Na panelu Snadné spuštění v části **Seznamy** zvolte **odkaz Kalendář.**

     Zobrazí **se stránka** Kalendář.

     Pokud se na panelu Snadné spuštění nezobrazí žádný odkaz Kalendář, zvolte odkaz **Obsah webu.** Pokud na stránce Obsah webu není položka **Kalendáře,** vytvořte ji.

3. Na stránce Kalendář zvolte den a pak  zvolte odkaz Přidat ve vybraném dni a přidejte událost.

4. Do **pole Název** zadejte **Ve výchozím kalendáři** zadejte Událost a pak zvolte **tlačítko** Uložit.

5. Zvolte odkaz **Obsah webu** a pak zvolte **dlaždici Přidat** aplikaci.

6. Na **stránce Vytvořit** zvolte Typ **kalendáře,** pojmete kalendář a pak zvolte **tlačítko** Vytvořit.

7. Přidejte událost do nového kalendáře, pojmechte událost **Event ve** vlastním kalendáři a pak zvolte **tlačítko** Uložit.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Přidání webové části na stránku webové části

1. Na stránce **Obsah webu** otevřete složku **Stránky webu.**

2. Na pásu karet zvolte **kartu Soubory,** otevřete **nabídku Nový** dokument a pak zvolte příkaz **Stránka webové části.**

3. Na stránce **Nová stránka webové části** pojmete stránku **SampleWebPartPage.aspx** a pak zvolte **tlačítko** Vytvořit.

     Zobrazí se stránka webové části.

4. V horní zóně stránky webové části zvolte kartu **Vložit** a pak zvolte **tlačítko Webová** část.

5. Zvolte **složku Vlastní,** zvolte webovou část **VisualWebPart1** a pak zvolte **tlačítko** Přidat.

     Webová část se zobrazí na stránce. Na webové části se zobrazí následující ovládací prvky:

    - Zobrazení měsíčního kalendáře.

    - Tlačítko  Aktualizovat.

    - Zaškrtávací **políčko** Kalendář.

    - Zaškrtávací **políčko Vlastní** kalendář.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Určení seznamů, které se mají zahrnout do zobrazení měsíčního kalendáře

Ve webové části zadejte kalendáře, které chcete zahrnout do zobrazení měsíčního kalendáře, a pak zvolte **tlačítko** Aktualizovat.

Události ze všech kalendářů, které jste zadali, se zobrazí v zobrazení měsíčního kalendáře.

## <a name="see-also"></a>Viz také

[Vytváření webových částí pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Návod: Vytvoření webové části pro SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
