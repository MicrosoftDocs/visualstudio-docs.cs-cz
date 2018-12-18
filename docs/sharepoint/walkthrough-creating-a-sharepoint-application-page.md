---
title: 'Návod: Vytvoření stránky aplikace služby SharePoint | Dokumentace Microsoftu'
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
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52ff6b3431ac3f87c85eefcf728cfe4c4875f884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634784"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Návod: Vytvoření stránky aplikace služby SharePoint
 
Stránka aplikace je specializovaná forma stránky technologie ASP.NET. Stránky aplikace obsahují obsah, který je sloučen s hlavní stránkou služby SharePoint. Další informace najdete v tématu [vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Tento návod ukazuje, jak vytvořit stránku aplikace a pak ho ladit pomocí místního webu služby SharePoint. Tato stránka zobrazuje všechny položky, které každý uživatel vytvořil nebo změnil na všech serverech ve farmě.

Tento návod znázorňuje následující úlohy:

- Vytvoření projektu služby SharePoint.
- Přidání stránky aplikace do projektu služby SharePoint.
- Přidání ovládacích prvků ASP.NET na stránku aplikace.
- Přidání kódu na pozadí ovládacích prvků technologie ASP.NET.
- Testování stránky aplikace.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

- Podporované edice systému Windows a SharePoint.

## <a name="create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint

Nejprve vytvořte **prázdný projekt SharePoint**. Později budete přidávat **stránky aplikace** položku do tohoto projektu.

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Otevřít **nový projekt** dialogového okna rozbalte **Office/SharePoint** uzel v jazyce, který chcete použít a klikněte na tlačítko **řešení služby SharePoint** uzlu.

3. V **nainstalované šablony Visual Studio** podokně, vyberte **SharePoint 2010 - prázdný projekt** šablony. Pojmenujte projekt **MySharePointProject**a klikněte na tlačítko **OK** tlačítko.

     **Průvodce přizpůsobením SharePoint** se zobrazí. Tento průvodce vám umožní vybrat web, který budete používat k ladění projektu a úroveň důvěryhodnosti řešení.

4. Zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko k přijetí výchozího místního webu služby SharePoint.

## <a name="create-an-application-page"></a>Vytvoření stránky aplikace

Chcete-li vytvořit stránku aplikace, přidejte **stránky aplikace** položky do projektu.

1. V **Průzkumníka řešení**, zvolte **MySharePointProject** projektu.

2. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

3. V **přidat novou položku** dialogového okna zvolte **stránka aplikace (pouze řešení farmy** šablony.

4. Pojmenujte stránku **SearchItems**a klikněte na tlačítko **přidat** tlačítko.

     Návrhář Visual Web Developer zobrazí stránku aplikace v **zdroj** zobrazení, kde můžete zobrazit elementy na stránce HTML. Návrhář zobrazí značky pro několik <xref:System.Web.UI.WebControls.Content> ovládacích prvků. Každý ovládací prvek mapuje <xref:System.Web.UI.WebControls.ContentPlaceHolder> ovládací prvek, který je definován na výchozí stránce předlohy aplikace.

## <a name="design-the-layout-of-the-application-page"></a>Návrh rozložení stránky aplikace

Položka stránka aplikace umožňuje používat návrháře přidat ovládací prvky ASP.NET na stránku aplikace. Tento návrhář je stejný jako ten použít v aplikaci Visual Web Developer. Přidejte popisek, seznam přepínačů a tabulku, aby **zdroj** návrháře a potom nastavte vlastnosti stejně jako při návrhu jakékoli standardní stránky technologie ASP.NET.

1. V panelu nabídky zvolte **zobrazení** > **nástrojů**.

2. V uzlu standardní **nástrojů**, proveďte jednu z následujících kroků:

    - Otevřete místní nabídku pro **popisek** položky, zvolte **kopírování**, otevřete místní nabídku pro řádek u **PlaceHolderMain** obsah ovládacího prvku v návrháři a pak Zvolte **vložit**.

    - Přetáhněte **popisek** položky **nástrojů** do těla **PlaceHolderMain** ovládacího prvku obsahu.

3. Opakujte předchozí krok a přidejte **DropDownList** položky a **tabulky** položkou **PlaceHolderMain** ovládacího prvku obsahu.

4. V Návrháři změňte hodnotu `Text` atribut ovládacího prvku popisku **zobrazit všechny položky**.

5. V Návrháři nahraďte `<asp:DropDownList>` element s následující kód XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Zpracování událostí ovládacích prvků na stránce

Zpracování ovládacích prvků na stránce aplikace, stejně jako jakékoli stránky technologie ASP.NET. V tomto postupu zpracujete `SelectedIndexChanged` události z rozevíracího seznamu.

1. Na **zobrazení** nabídce zvolte **kód**.

     Soubor kódu stránky aplikace se otevře v editoru kódu.

2. Přidejte následující metodu do `SearchItems` třídy. Tento kód zpracovává <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> událost <xref:System.Web.UI.WebControls.DropDownList> voláním metody, kterou vytvoříte později v tomto názorném postupu.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Do horní části souboru kódu stránky aplikace přidejte následující příkazy.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Přidejte následující metodu do `SearchItems` třídy. Tato metoda projde všechny servery ve farmě a vyhledá položky vytvořené nebo změněné aktuálním uživatelem.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Přidejte následující metodu do `SearchItems` třídy. Tato metoda zobrazí položky vytvořené nebo změněné aktuálním uživatelem v tabulce.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Otestování stránky aplikace

Při spuštění projektu se otevře web služby SharePoint a zobrazí se stránka aplikace.

1. V **Průzkumníka řešení**, otevřete místní nabídku pro stránku aplikace a klikněte na tlačítko **nastavit jako položku při spuštění**.

2. Zvolte **F5** klíč.

     Otevře se web služby SharePoint.

3. Na stránce aplikace vyberte **změněny mnou** možnost.

     Stránka aplikace se aktualizuje a zobrazí všechny položky, které jste upravili ve všech serverech ve farmě.

4. Na stránce aplikace vyberte **mnou vytvořené** v seznamu.

     Stránka aplikace se aktualizuje a zobrazí všechny položky, které jste vytvořili ve všech serverech ve farmě.

## <a name="next-steps"></a>Další kroky

Další informace o použití stránek služby SharePoint, naleznete v tématu [vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Vám může Další informace o navrhování obsahu stránky služby SharePoint pomocí Visual Web Designer z těchto témat:

- [Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Viz také:

[Postupy: vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)  
[Typ stránky _layouts aplikace](http://go.microsoft.com/fwlink/?LinkID=169274)
