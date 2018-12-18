---
title: 'Návod: Import položek z existující stránky SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86256cdecd878c78c34d7128a05eb7b795067701
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909754"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Návod: Import položek z existující stránky SharePoint
  Tento návod ukazuje, jak importovat položky z existující stránky SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.  
  
 Tento návod demonstruje následující úkoly:  
  
- Přizpůsobení webu služby SharePoint tak, že přidáte vlastní sloupec (označované také jako *pole*.  
  
- Export do souboru WSP webu služby SharePoint.  
  
- Import souboru WSP do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sharepointu s použitím Importovat projekt WSP.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.  
  
-   Visual Studio.  
  
## <a name="customize-a-sharepoint-site"></a>Přizpůsobení webu služby SharePoint
 V tomto příkladu vytvoříte a přizpůsobit podřízeného webu služby SharePoint přidáním nového sloupce webu a vytvořením další podřízené lokality pro pozdější použití. Později bude první podřízený web exportovat do souboru WSP a importujte vlastní sloupec druhý podřízený web pomocí .wsp Importovat projekt.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>K vytváření a přizpůsobování webu služby SharePoint  
  
1. Otevřete web služby SharePoint pomocí webového prohlížeče, třeba http://<em>systémový název</em>/SitePages/Home.aspx.  
  
2. Vytvořit podřízený web z hlavního webu služby SharePoint tak, že otevřete **Akce webu** nabídky a následným výběrem možnosti **novou lokalitu**.  
  
3. Na webu **vytvořit** dialogového okna zvolte **prázdný web** typu.  
  
4. V **Title** zadejte **lokality sloupec Test 1**; v **název adresy URL** zadejte **columntest1**; ostatní nastavení ponechte jejich výchozí hodnoty. a klikněte na tlačítko **vytvořit** tlačítko.  
  
5. Po vytvoření webu, přejděte v prohlížeči zpět na hlavní stránku http://<em>systémový název</em>/SitePages/Home.aspx.  
  
6. Znovu vytvořit prázdné podřízenou lokalitu z hlavního webu služby SharePoint tak, že otevřete **Akce webu** nabídky, výběr **novou lokalitu**a potom kliknete **prázdný web** typu.  
  
7. V **Title** zadejte **lokality sloupec Test 2**; v **název adresy URL** zadejte **columntest2**; ostatní nastavení ponechte jejich výchozí hodnoty. a klikněte na tlačítko **vytvořit** tlačítko.  
  
8. Přejděte zpět na první podřízený http://<em>SystemName</em>/columntest1/default.aspx.  
  
9. Na **Akce webu** nabídce zvolte **nastavení webu** zobrazíte na stránce Nastavení lokality.  
  
10. V **Galerie** zvolte **sloupce webu** odkaz.  
  
11. V horní části **sloupec galerii** zvolte **vytvořit** tlačítko.  
  
12. V **název sloupce** zadejte **Test sloupec**, ponechte výchozí hodnoty a klikněte na tlačítko **OK** tlačítko.  
  
13. **Test sloupec** sloupce se zobrazí ve sloupci vlastní nadpis v galerii sloupce webu.  
  
## <a name="exporting-the-sharepoint-site"></a>Export webu služby SharePoint
 V dalším kroku získat soubor nastavení (.wsp) služby SharePoint, který obsahuje položky služby SharePoint a prvků, které chcete importovat do vaší [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint. Pokud již nemáte soubor WSP, pak musíte vytvořit jeden z existující stránky SharePoint. V tomto příkladu budete exportovat výchozí web služby SharePoint do souboru WSP.  
  
> [!IMPORTANT]  
>  Pokud se zobrazí chyba za běhu provedením následujících kroků, budete muset provést postup v systému, který má přístup k webu služby SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Chcete-li exportovat existující stránky SharePoint  
  
1.  Na webu služby SharePoint zvolte **nastavení webu** na **Akce webu** karet zobrazit na stránce Nastavení lokality.  
  
2.  V **Akce webu** části stránky nastavení webu, zvolte **web uložit jako šablonu** odkaz.  
  
3.  V **název_souboru** zadejte **ExampleSite**a **název šablony** zadejte **lokality příklad**.  
  
4.  V tomto příkladu ponechte **zahrnout obsah** zrušte zaškrtnutí políčka.  
  
     Pokud zaškrtnete toto políčko [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uloží všechny seznamy a knihovny dokumentů a jejich obsah do souboru WSP. I když to je užitečné v některých případech, to není nutné v tomto příkladu.  
  
5.  Po dokončení operace úspěšně, zvolte **Galerie řešení** odkaz k zobrazení souboru WSP.  
  
     Chcete-li zobrazit stránku Galerie řešení novější, otevřete **Akce webu** nabídce zvolte **nastavení webu**, zvolte **přejděte na nastavení lokality nejvyšší úrovně** odkaz v  **Správa kolekce lokalit** části a klikněte na tlačítko **řešení** odkaz v **Galerie** oddílu.  
  
6.  V Galerii řešení zvolte **ExampleSite** odkaz.  
  
7.  V **stažení souboru** dialogového okna zvolte **Uložit** tlačítko pro uložení souboru v místním systému, ve výchozím nastavení se ve složce stažené soubory.  
  
## <a name="import-the-wsp-file"></a>Import souboru WSP
 Teď, když máte *.wsp* soubor, který obsahuje položky, kterou chcete znovu použít (vlastní sloupec webu testovací sloupec), importovat *.wsp* souboru k němu přistupovat.  
  
#### <a name="to-import-a-wsp-file"></a>Import souboru WSP  
  
1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na panelu nabídek zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt**dialogové okno. Pokud vaše rozhraní IDE nastaveno pro použití vývojového nastavení jazyka Visual Basic, v řádku nabídek, zvolte **souboru** > **nový projekt**.  
  
2. Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3. Zvolte **importovat balíček řešení služby SharePoint 2010** šablony **šablony** podokno, ponechte název projektu jako WspImportProject1 a klikněte na tlačítko **OK** tlačítko.  
  
    **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
4. Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pro druhý podřízeného webu služby SharePoint, který jste vytvořili dříve. Přidejte nová vlastní pole položek, http://<em>systémový název</em>/columntest2 tento podřízený web.  
  
5. V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** části, nechte vybranou volbu **nasadit jako řešení v izolovaném prostoru**.  
  
6. V **zadat nový zdroj projektu** stránce, přejděte do umístění v systému, kam jste uložili *.wsp* dříve souboru a klikněte na tlačítko **Další** tlačítko.  
  
   > [!NOTE]  
   >  Pokud se rozhodnete **Dokončit** tlačítko na této stránce, všechny dostupné položky v *.wsp* naimportuje soubor.  
  
7. V **vybrat položky k importu** pole, zrušte zaškrtnutí všech políček v seznamu, s výjimkou **Test sloupec**a klikněte na tlačítko **Dokončit** tlačítko.  
  
    Vzhledem k tomu, že seznam obsahuje mnoho položek, můžete použít **Ctrl**+**A** klíče vybrat všechny položky v seznamu, zvolte klávesu MEZERNÍK a zrušte zaškrtnutí všech políček a pak vyberte pouze kontroly vedle pole **Test sloupec** položky.  
  
    Po dokončení operace importu nového projektu s názvem **WspImportProject1** se vytvoří, která obsahuje složku s názvem **pole**. V této složce je vlastní sloupec **Test sloupec** a jeho soubor definice *Elements.xml*.  
  
## <a name="deploy-the-project"></a>Nasazení projektu
 Nakonec nasazení **WspImportProject1** na druhý server SharePoint podřízeného webu, kterou jste dříve vytvořili vlastní sloupec zobrazení.  
  
#### <a name="to-deploy-the-project"></a>K nasazení projektu  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], zvolte **F5** klíč nasadit a spustit *.wsp* Importovat projekt.  
  
2.  Na webu služby SharePoint otevřete **Akce webu** nabídky a klikněte na tlačítko **nastavení webu** zobrazíte na stránce Nastavení lokality.  
  
3.  V **Galerie** zvolte **sloupce webu** odkaz.  
  
4.  Přejděte dolů k položce **vlastní sloupce** oddílu.  
  
     Všimněte si, že sloupec vlastního webu, který jste naimportovali z první web služby SharePoint se zobrazí v seznamu.  
  
## <a name="see-also"></a>Viz také:
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
