---
title: 'Návod: import položek z existujícího webu služby SharePoint | Microsoft Docs'
titleSuffix: ''
description: V tomto návodu importujte položky z existujícího webu služby SharePoint do projektu služby Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 861b6ff20f9ceb73c279e54fa89ee513389b6b91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900960"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Návod: import položek z existujícího webu služby SharePoint
  Tento návod ukazuje, jak importovat položky z existujícího webu služby SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.

 Tento názorný postup ukazuje následující úlohy:

- Přizpůsobení webu služby SharePoint přidáním vlastního sloupce webu (označuje se také jako *pole*.

- Export webu služby SharePoint do souboru WSP.

- Import souboru. wsp do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] služby SharePoint pomocí projektu importu. wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio

## <a name="customize-a-sharepoint-site"></a>Přizpůsobení webu služby SharePoint
 V tomto příkladu vytvoříte a přizpůsobíte podřízený web služby SharePoint přidáním nového sloupce webu do něj a vytvořením dalšího podřízeného webu pro pozdější použití. Později exportujte první podlokalitu do souboru. wsp a potom do druhého podřízeného webu importujte sloupec vlastní web pomocí projektu importu. wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Vytvoření a přizpůsobení webu služby SharePoint

1. Otevřete web služby SharePoint pomocí webového prohlížeče, například http://<em>System Name</em>/SitePages/Home.aspx.

2. Vytvořte podřízený web z hlavního webu služby SharePoint tak, že otevřete nabídku **Akce webu** a kliknete na možnost **Nový web**.

3. V dialogovém okně **vytvořit** lokalitu vyberte **prázdný typ webu** .

4. Do pole **název** zadejte **test sloupce webového serveru 1**; do pole **název adresy URL** zadejte **columntest1**; Ostatní nastavení ponechte na jejich výchozích hodnotách. a pak klikněte na tlačítko **vytvořit** .

5. Po vytvoření lokality přejděte v prohlížeči zpátky do hlavní lokality, http://<em>systémový název</em>/SitePages/Home.aspx.

6. Znovu vytvořte prázdný podřízený web z hlavního webu služby SharePoint tak, že otevřete nabídku **Akce webu** , zvolíte možnost **Nový web** a pak zvolíte **prázdný typ webu** .

7. Do pole **název** zadejte **test sloupce webu 2**; do pole **název adresy URL** zadejte **columntest2**; Ostatní nastavení ponechte na jejich výchozích hodnotách. a pak klikněte na tlačítko **vytvořit** .

8. Přejděte zpět na první podlokalitu, http://<em>System</em>/columntest1/default.aspx.

9. V nabídce **Akce webu** vyberte **nastavení lokality** , aby se zobrazila stránka nastavení webu.

10. V části **Galerie** vyberte odkaz **sloupce webu** .

11. V horní části stránky **Galerie sloupců webu** klikněte na tlačítko **vytvořit** .

12. Do pole **název sloupce** zadejte **sloupec test**, ponechte ostatní výchozí hodnoty a pak klikněte na tlačítko **OK** .

13. Sloupec **test** sloupce se zobrazí v záhlaví vlastních sloupců v galerii sloupců webu.

## <a name="exporting-the-sharepoint-site"></a>Export webu služby SharePoint
 Dále Získejte soubor instalace služby SharePoint (. wsp), který obsahuje položky a prvky služby SharePoint, které chcete importovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint. Pokud soubor. wsp ještě nemáte, musíte ho vytvořit z existujícího webu SharePoint. V tomto příkladu budete exportovat výchozí web služby SharePoint do souboru. wsp.

> [!IMPORTANT]
> Pokud se zobrazí chyba modulu runtime provedením následujícího postupu, je nutné provést postup v systému, který má přístup k webu služby SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Export existujícího webu služby SharePoint

1. Na webu služby SharePoint vyberte na kartě **Akce webu** možnost **Nastavení webu** a zobrazte stránku nastavení webu.

2. V části **Akce webu** na stránce nastavení lokality vyberte odkaz **Uložit web jako šablonu** .

3. Do pole **název souboru** zadejte **ExampleSite** a do pole **název šablony** zadejte **příklad site**.

4. V tomto příkladu ponechejte zaškrtávací políčko **Zahrnout obsah** nejasné.

     Pokud toto políčko zaškrtnete, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uloží všechny seznamy a knihovny dokumentů a jejich obsah do souboru. wsp. I když je to v některých případech užitečné, není to v tomto příkladu nutné.

5. Po úspěšném dokončení operace klikněte na odkaz **Galerie řešení** , abyste zobrazili soubor. wsp.

     Chcete-li zobrazit stránku galerie řešení později, otevřete nabídku **Akce webu** , zvolte **možnost nastavení webu**, zvolte odkaz **Přejít na nejvyšší úroveň Site Settings** v části **Správa kolekce webů** a pak zvolte odkaz **řešení** v části **Galerie** .

6. V galerii řešení klikněte na odkaz **ExampleSite** .

7. V dialogovém okně **Stažení souboru** klikněte na tlačítko **Uložit** a uložte soubor do místního systému ve výchozím nastavení ve složce stažené soubory.

## <a name="import-the-wsp-file"></a>Import souboru. wsp
 Teď, když máte soubor *. wsp* obsahující položku, kterou chcete znovu použít (sloupec test vlastního sloupce webu), importujte soubor *. wsp* pro přístup k němu.

### <a name="to-import-a-wsp-file"></a>Import souboru. wsp

1. V aplikaci klikněte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na panelu nabídek na položku **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** . Pokud je vaše rozhraní IDE nastaveno na použití Visual Basic vývojové nastavení, na panelu nabídky vyberte **soubor**  >  **Nový projekt**.

2. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. Zvolte šablonu **balíčku řešení pro import sady SharePoint 2010** v podokně **šablony** , ponechte název projektu jako WspImportProject1 a pak klikněte na tlačítko **OK** .

    Zobrazí se **Průvodce přizpůsobením SharePointu** .

4. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pro druhý podřízený web služby SharePoint, který jste vytvořili dříve. Do této dílčí lokality přidáte novou položku vlastního pole http://<em>System Name</em>/columntest2.

5. V části **co je úroveň důvěryhodnosti tohoto řešení služby SharePoint?** ponechte výběr jako **nasadit jako řešení v izolovaném prostoru (sandbox)**.

6. Na stránce **zadat zdroj nového projektu** vyhledejte umístění v systému, kam jste dříve uložili soubor *. wsp* , a poté klikněte na tlačítko **Další** .

   > [!NOTE]
   > Pokud na této stránce kliknete na tlačítko **Dokončit** , naimportují se všechny dostupné položky v souboru *. wsp* .

7. V poli **Vybrat položky k importu** zrušte zaškrtnutí všech políček v seznamu s výjimkou **sloupce test** a potom klikněte na tlačítko **Dokončit** .

    Vzhledem k tomu, že seznam obsahuje mnoho položek, můžete zvolit možnost **kláves CTRL** + **a** vybrat všechny položky v seznamu, zvolit klávesu MEZERNÍK pro zrušení zaškrtnutí všech políček a pak zaškrtnout políčko vedle položky **sloupce testu** .

    Po dokončení operace importu se vytvoří nový projekt s názvem **WspImportProject1** , který obsahuje složku s názvem **pole**. V této složce je **sloupec test** sloupce vlastního webu a jeho definiční soubor *Elements.xml*.

## <a name="deploy-the-project"></a>Nasadit projekt
 Nakonec nasaďte **WspImportProject1** na druhý podřízený web služby SharePoint, který jste vytvořili dříve pro zobrazení sloupce vlastní web.

### <a name="to-deploy-the-project"></a>Nasazení projektu

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] klikněte na klávesu **F5** pro nasazení a spuštění projektu importu *. wsp* .

2. Na webu služby SharePoint otevřete nabídku **Akce webu** a pak zvolte možnost **Nastavení webu** . zobrazí se stránka nastavení webu.

3. V části **Galerie** vyberte odkaz **sloupce webu** .

4. Přejděte dolů do části **vlastní sloupce** .

     Všimněte si, že se v seznamu zobrazí sloupec vlastní web, který jste importovali z prvního webu služby SharePoint.

## <a name="see-also"></a>Viz také
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
