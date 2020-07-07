---
title: Importovat vlastní stránku & stránky webu s obrázkem
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 311124b2e0b81e70c4c2a7b40754207e6c66b749
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015686"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Návod: import vlastní stránky předlohy a stránky webu s obrázkem
  Tento návod ukazuje, jak importovat vlastní stránku předlohy služby SharePoint a stránku webu, která obsahuje obrázek do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.

 Tento návod ukazuje, jak provádět následující úlohy:

- Vytvoření vlastní stránky předlohy a stránky webu pomocí obrázku v aplikaci SharePoint Designer.

- Exportujte vlastní stránku předlohy, obrázek a stránku webu do souboru řešení služby SharePoint (*. wsp*).

- Importujte a nasaďte soubor *. wsp* do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint pomocí projektu Import balíčku řešení služby SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto Názorného postupu musíte mít následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Vytváření položek v SharePoint designeru
 Tento příklad ukazuje, jak vytvořit tři položky v Návrháři SharePoint pro export: vlastní stránku předlohy, stránku lokality, která odkazuje na vlastní stránku předlohy, a soubor obrázku, který se má zobrazit na stránce webu. Obrázek se přidá do složky/images/na SharePointu.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Vytvoření vlastní stránky předlohy v Návrháři služby SharePoint

1. V Návrháři služby SharePoint v navigačním podokně vyberte objekt lokality **hlavní stránky** .

2. Na pásu karet **stránky předlohy** vyberte možnost **prázdná stránka předlohy**.

3. Zvolte novou stránku předlohy a pak na pásu karet **stránky předlohy** zvolte **Upravit soubor**.

4. V dolní části návrháře služby SharePoint klikněte na kartu **kód** .

5. Nahraďte existující kód následujícím kódem.

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

6. Uložte stránku, klikněte na kartu **stránky předlohy** a přejmenujte stránku předlohy jako **mybasic1. Master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Přidání obrázku do databáze obsahu v Návrháři služby SharePoint
 Nyní můžete přidat obrázek, který se zobrazí na stránce webu. Bitová kopie je nasazena do databáze obsahu služby SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Přidání obrázku do databáze obsahu v Návrháři služby SharePoint

1. V navigačním podokně zvolte objekt lokality **všechny soubory** a potom ve stromovém zobrazení zvolte složku **obrázky** .

2. Na pásu karet **všechny soubory** zvolte možnost **importovat soubory**, zvolte požadovaný soubor a pak klikněte na tlačítko **OK** . V tomto příkladu je soubor pojmenován **myimg1.png**.

     Volitelně můžete vytvořit podsložku, která bude lépe organizovat obrázky.

3. Zavřete dialogové okno **Import** .

## <a name="create-a-site-page"></a>Vytvoření stránky webu
 Tato stránka základního webového serveru používá vlastní stránku předlohy a zobrazuje obrázek, který jste přidali v předchozím kroku.

#### <a name="to-create-a-site-page"></a>Vytvoření stránky webu

1. V navigačním podokně vyberte objekt **stránky webu** .

2. Na pásu karet **stránky** klikněte na tlačítko **Stránka** , zvolte typ stránky **aspx** a potom zadejte název nového souboru **MyContentPage1. aspx**.

     Volitelně můžete vytvořit podsložku, která bude pomáhat organizovat stránky webu.

3. V seznamu stránky webu zvolte **MyContentPage1. aspx** , otevřete stránku vlastností a potom v dolní části stránky klikněte na odkaz **Upravit soubor** .

     Pokud se zobrazí zpráva s oznámením, že tato stránka neobsahuje žádné oblasti, které lze upravovat v bezpečném režimu, a zeptá se, jestli chcete otevřít tuto stránku v rozšířeném režimu, klikněte na tlačítko **Ano** .

4. V dolní části stránky klikněte na tlačítko **kód** .

5. Nahraďte existující kód následujícím kódem.

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

6. Uložte aktualizovanou stránku webu.

## <a name="export-the-items-from-sharepoint"></a>Exportovat položky ze SharePointu
 Exportujte položky ze SharePointu do souboru řešení služby SharePoint (*. wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Export položek z aplikace SharePoint Designer

1. V Návrháři služby SharePoint v navigačním podokně zvolte objekt **týmového webového serveru** a poté na pásu karet **Web** zvolte možnost **Uložit jako šablonu**.

2. V dialogovém okně **Uložit jako šablonu** zadejte název souboru a název šablony, zaškrtněte políčko **Zahrnout obsah** a pak klikněte na tlačítko **OK** .

     Tím se uloží obsah webu v souboru *WSP* .

3. Po exportu řešení vyberte odkaz **Galerie řešení** a zobrazte seznam dostupných souborů řešení.

4. Otevřete místní nabídku nového souboru *WSP* a zvolte možnost **Uložit cíl jako** a uložte ji do systému.

## <a name="import-the-items-into-visual-studio"></a>Import položek do sady Visual Studio
 Importujte soubor *. wsp* do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Po importu obsahu ho můžete přizpůsobit, přidat další položky a pak ho nasadit.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Import položek ze souboru. wsp do sady Visual Studio

1. V nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt **importu balíčku řešení SharePoint 2010** .

2. Na stránce **Vybrat položky, které mají být importovány** v části **modul** ve sloupci **typ** zaškrtněte políčka pro import pouze ze souborů v následující tabulce.

   | Název souboru | Popis |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Vlastní stránka předlohy. |
   | images_ | Soubor bitové kopie v systému souborů SharePoint. |
   | SitePages_ | Stránka webu. |

3. Kliknutím na tlačítko **Dokončit** naimportujete vybrané položky.

4. V **Průzkumník řešení**vyberte \_ \_ uzel catalogsmasterpage a nastavte hodnotu vlastnosti **řešení konfliktů nasazení** na hodnotu **automaticky**.

    To pomáhá zajistit, aby byly všechny konflikty nasazení vyřešeny automaticky.

5. Pokud má nová stránka předlohy stejný název jako existující stránka, ujistěte se, že existující stránka není označena jako výchozí stránka předlohy nebo vlastní stránka předlohy v Návrháři služby SharePoint.

    Pokud je existující stránka předlohy označená jako výchozí stránka předlohy nebo vlastní stránka předlohy, zobrazí se chyba nasazení, která uvádí, že nelze odstranit hlavní stránku. Chcete-li se tomuto problému vyhnout, postupujte takto:

   - Pokud je existující stránka předlohy nastavena jako výchozí stránka předlohy, dočasně nastavte jinou stránku předlohy jako výchozí stránku předlohy. Po nasazení souborů do služby SharePoint nastavte novou stránku předlohy jako výchozí stránku předlohy.

   - Pokud je existující stránka předlohy nastavena jako vlastní stránka předlohy, dočasně nastavte jinou stránku předlohy jako vlastní stránku předlohy. Po nasazení souborů do služby SharePoint nastavte novou stránku předlohy jako vlastní stránku předlohy.

6. Na panelu nabídek vyberte **sestavení**  >  **nasadit řešení**.

7. Otevřete web služby SharePoint pro zobrazení nasazených položek.

   Alternativní způsob importu souborů do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] služby SharePoint a jejich nasazení do služby SharePoint je přidání souborů do modulů v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Postupy: Import stránky předlohy nebo motivu](../sharepoint/how-to-import-a-master-page-or-theme.md) a [použití modulů k zahrnutí souborů v řešení](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Viz také:
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
