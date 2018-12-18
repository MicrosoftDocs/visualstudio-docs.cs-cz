---
title: 'Návod: Import vlastní stránky předlohy a stránky webu s bitovou kopii | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 45f1ded9cf6eca3715c5050f93aa24630a1bc4e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890984"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Návod: Importujte vlastní stránky předlohy a stránky webu s obrázkem
  Tento návod ukazuje, jak importovat vlastní stránku SharePoint předlohy a stránky webu s obrázkem do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.  

 Tento návod ukazuje, jak provádět následující úlohy:  

- Vytvoření vlastní stránky předlohy a stránky webu s použitím image v SharePoint designeru.  

- Exportovat vlastní stránku předlohy, image a stránku webu do řešení služby SharePoint (*.wsp*) soubor.  

- Importujte a nasaďte *.wsp* do souboru [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint pomocí aplikace project importovat balíček řešení služby SharePoint.  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>Požadavky  
 Musíte mít následující součásti k dokončení tohoto návodu:  

-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.  

-   Visual Studio.  

-   SharePoint Designer 2010.  

## <a name="create-items-in-sharepoint-designer"></a>Vytvoření položek v aplikaci SharePoint Designer
 Tento příklad ukazuje, jak vytvořit tři položky v SharePoint designeru pro export: vlastní stránku předlohy, stránku webu, který odkazuje na vlastní stránky předlohy a souboru obrázku, který se zobrazí na stránce webu. Na obrázku je přidána do /images/ složky v Sharepointu.  

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Chcete-li vytvořit vlastní stránku předlohy v aplikaci SharePoint Designer

1.  V aplikaci SharePoint Designer, vyberte v navigačním podokně **stránky předlohy** objektu lokality.  

2.  Na **stránky předlohy** pásu karet, zvolte **prázdnou stránku předlohy**.  

3.  Zvolte nové stránky předlohy a potom na **stránky předlohy** pásu karet, zvolte **upravit soubor**.  

4.  V dolní části návrháře služby SharePoint, zvolte **kód** kartu.  

5.  Nahraďte stávající kód následujícím kódem.  

    ```aspx-csharp  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  

6.  Uložit na stránku, zvolte **stránky předlohy** kartu a přejmenovat na hlavní stránce jako **mybasic1.master**.  

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Přidání obrázku na databázi obsahu v aplikaci SharePoint Designer
 Nyní můžete přidat obrázek, který se zobrazí na stránce webu. Image bude nasazena na databázi obsahu služby SharePoint.  

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Chcete-li přidat bitovou kopii do databáze obsahu v aplikaci SharePoint Designer

1.  V navigačním podokně, vyberte **všechny soubory** lokality objektu a zvolte ve stromovém zobrazení klikněte **imagí** složky.  

2.  Na **všechny soubory** pásu karet, zvolte **Import souborů**, zvolte soubor podle vašeho výběru a klikněte na tlačítko **OK** tlačítko. V tomto příkladu je název souboru **myimg1.png**.  

     Volitelně můžete vytvořit podsložku kvůli lepší organizaci bitové kopie.  

3.  Zavřít **Import** dialogové okno.  

## <a name="create-a-site-page"></a>Vytvoření stránky webu
 Tato stránka základního webu používá vlastní stránky předlohy a zobrazí obrázek, který jste přidali v předchozím kroku.  

#### <a name="to-create-a-site-page"></a>Chcete-li vytvořit stránku webu  

1.  V navigačním podokně, vyberte **stránky webu** objektu.  

2.  Na **stránky** pásu karet, zvolte **stránky** tlačítko, zvolte **ASPX** typ stránky a potom zadejte název nového souboru **mycontentpage1.aspx**.  

     Volitelně můžete vytvořit podsložku kvůli lepší organizaci stránky webu.  

3.  V seznamu stránek webu zvolte **MyContentPage1.aspx** otevřete jeho stránku vlastností a pak v dolní části stránky zvolte **upravit soubor** odkaz.  

     Pokud zpráva se zobrazí a říká, že tato stránka neobsahuje žádné oblasti, které lze upravit v nouzovém režimu a zeptá, jestli chcete tuto stránku otevřít v rozšířeném režimu, zvolte **Ano** tlačítko.  

4.  V dolní části stránky zvolte **kód** tlačítko.  

5.  Nahraďte stávající kód následujícím kódem.  

    ```aspx-csharp  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  

6.  Uložte aktualizovaný web stránky.  

## <a name="export-the-items-from-sharepoint"></a>Export položek ze Sharepointu
 Export položek ze Sharepointu do řešení služby SharePoint (*.wsp*) soubor.  

#### <a name="to-export-items-from-sharepoint-designer"></a>Export položky z aplikace SharePoint Designer

1.  V aplikaci SharePoint Designer, vyberte v navigačním podokně **týmový web** objektu a potom na **lokality** pásu karet, zvolte **uložit jako šablonu**.  

2.  V **uložit jako šablonu** dialogového okna zadejte název souboru a název šablony, vyberte **zahrnout obsah** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  

     Tato akce uloží obsah lokality *.wsp* souboru.  

3.  Až se exportuje řešení, zvolte **Galerie řešení** odkaz zobrazíte seznam souborů k dispozici řešení.  

4.  Otevřete místní nabídku pro nový *.wsp* souboru a klikněte na tlačítko **Uložit cíl jako** ji uložit do systému.  

## <a name="import-the-items-into-visual-studio"></a>Importovat položky do sady Visual Studio
 Import *.wsp* soubor do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po importu obsahu můžete přizpůsobit ji, přidat další položky a potom ji nasadíte.  

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Import položek ze souboru WSP do sady Visual Studio  

1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvořte **importovat balíček řešení služby SharePoint 2010** projektu.  

2. Na **vybrat položky k importu** stránce v části **modulu** v **typ** sloupců, zaškrtněte políčka pro pouze soubory v následující tabulce pro import.  


   | Název souboru | Popis |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Vlastní stránky předlohy. |
   | images_ | Soubor obrázku v systému souborů služby SharePoint. |
   | SitePages_ | Stránka webu. |


3. Zvolte **Dokončit** tlačítko Import vybraných položek.  

4. V **Průzkumníka řešení**, zvolte \_catalogsmasterpage\_ uzel a nastavte hodnotu jeho **řešení konfliktů při nasazení** vlastnost **automatické** .  

    To pomáhá zajistit, že všechny konflikty nasazení jsou řešeny automaticky.  

5. Pokud vaše nová stránka předlohy má stejný název jako existující stránky, ujistěte se, že existující stránky není označena jako hlavní stránky výchozí nebo vlastní stránky předlohy v SharePoint designeru.  

    Pokud stávající stránky předlohy je označená jako výchozí stránky předlohy nebo vlastní stránky předlohy, zobrazí se chyba nasazení, která uvádí, že nelze odstranit stránky předlohy. Chcete-li tomuto problému vyhnout, postupujte takto:  

   -   Pokud stávající stránky předlohy je nastavená na výchozí stránce předlohy, jiné stránky předlohy dočasně nastaví jako výchozí stránky předlohy. Poté, co nasadíte soubory do služby SharePoint, nastavte jako výchozí stránku předlohy nové stránky předlohy.  

   -   Pokud je existující stránky předlohy nastavená jako vlastní stránky předlohy, dočasně nastaví jiné stránky předlohy jako vlastní stránky předlohy. Poté, co nasadíte soubory do služby SharePoint, nastavení nové stránky předlohy jako vlastní stránky předlohy.  

6. V panelu nabídky zvolte **sestavení** > **nasadit řešení**.  

7. Otevřete web služby SharePoint k zobrazení nasazené položky.  

   Alternativní způsob importu souborů do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a nasazovat je do služby SharePoint, je přidat soubory do modulů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Postupy: Import stránky předlohy nebo motivu](../sharepoint/how-to-import-a-master-page-or-theme.md) a [vložení souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md).  

## <a name="see-also"></a>Viz také:
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  

