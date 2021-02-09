---
title: 'Postupy: lokalizace značek ASPX | Microsoft Docs'
description: Naučte se lokalizovat značky ASPX na SharePointu tak, že nahradíte pevně kódované řetězcové hodnoty výrazy, které odkazují na lokalizované prostředky.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1876e06348d60f8a960b352525fd72ad06795101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931731"
---
# <a name="how-to-localize-aspx-markup"></a>Postupy: lokalizace značek ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky (. aspx) obvykle používají pevně kódované řetězcové hodnoty. Chcete-li lokalizovat tyto řetězce, nahraďte je výrazy, které odkazují na lokalizované prostředky.

## <a name="localize-aspx-markup"></a>Lokalizace značek ASPX

#### <a name="to-localize-aspx-markup"></a>Lokalizace kódu ASPX

1. Přidejte samostatné soubory prostředků: jeden pro výchozí jazyk a jeden pro každý lokalizovaný jazyk.

     Pokud lokalizaci pouze kódu a nikoli kódu, přidejte položku projektu globální soubor prostředků. Pokud lokalizaci kódu a značky, přidejte položku projektu soubor prostředků.

    1. Chcete-li přidat soubor globálních prostředků, v **Průzkumník řešení** otevřete místní nabídku pro položku sharepointového projektu a pak zvolte možnost **Přidat**  >  **novou položku**. V uzlu SharePoint **2010** vyberte šablonu **souboru globálních zdrojů** .

    2. Chcete-li přidat soubor prostředků, v **Průzkumník řešení** otevřete místní nabídku pro položku sharepointového projektu a pak zvolte možnost **Přidat**  >  **novou položku**. V uzlu **Visual Basic** nebo **Visual C#** vyberte šablonu **soubor prostředků** .

    > [!NOTE]
    > Nezapomeňte přidat soubory prostředků do položky projektu služby SharePoint a povolit vlastnost typ nasazení. Tato vlastnost je povinná později v tomto postupu. Pokud vaše řešení neobsahuje položku SharePointového projektu, můžete přidat prázdný projekt SharePoint a odebrat jeho výchozí *Elements.xml* soubor.

2. Pojmenujte soubor prostředků výchozího jazyka názvem vaší volby, který je připojený s příponou *. resx* , jako je MyAppResources. resx. Použijte stejný základní název pro každý lokalizovaný soubor prostředků, ale přidejte jazykovou verzi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Například pojmenujte německý lokalizovaný prostředek *MyAppResources.de-de. resx*.

3. Změňte hodnotu vlastnosti **typ nasazení** každého souboru prostředků na **AppGlobalResource** , aby se mohly nasadit do složky App_GlobalResources serveru.

4. Pokud používáte prostředky k lokalizaci kódu kromě značek ASPX, ponechte hodnotu vlastnosti **Akce sestavení** každého souboru jako **vložený prostředek**. Pokud používáte soubory prostředků pouze k lokalizaci kódu, můžete volitelně změnit hodnotu vlastnosti souborů na **obsah**. Další informace najdete v tématu [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

5. Otevřete všechny soubory prostředků a v každém souboru přidejte lokalizované řetězce pomocí stejných ID řetězců.

6. V [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] kódu pro stránku ASPX nebo ovládací prvek nahraďte pevně kódované řetězce hodnotami, které jsou v následujícím formátu:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Například pro lokalizaci textu ovládacího prvku popisek na stránce aplikace byste změnili:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     na

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Kliknutím na klávesu **F5** sestavíte a spustíte aplikaci.

8. Ve službě SharePoint změňte jazyk zobrazení z výchozí hodnoty.

     Lokalizované řetězce se zobrazí v aplikaci. Chcete-li zobrazit lokalizované prostředky, musí mít server SharePoint nainstalovanou jazykovou sadu, která odpovídá jazykové verzi souboru prostředků.

## <a name="see-also"></a>Viz také
- [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Postupy: Lokalizace funkce](../sharepoint/how-to-localize-a-feature.md)
- [Postupy: Přidání souboru prostředků](../sharepoint/how-to-add-a-resource-file.md)
- [Postupy: Lokalizace kódu](../sharepoint/how-to-localize-code.md)
