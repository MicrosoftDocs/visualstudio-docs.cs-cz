---
title: 'Návod: Vytvoření stránky aplikace služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0eaf7bda4ac4ed67dae79b8dd83bb59ba6985343
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985030"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Návod: Vytvoření stránky aplikace služby SharePoint

Stránka aplikace je speciální forma stránky ASP.NET. Stránky aplikace obsahují obsah, který je sloučen se stránkou předlohy služby SharePoint. Další informace najdete v tématu [Vytvoření stránek aplikace pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Tento návod ukazuje, jak vytvořit stránku aplikace a jak ji ladit pomocí místního webu služby SharePoint. Tato stránka zobrazuje všechny položky, které každý uživatel vytvořil nebo upravil ve všech lokalitách na serverové farmě.

Tento návod znázorňuje následující úlohy:

- Vytvoření projektu služby SharePoint.
- Přidání stránky aplikace do projektu služby SharePoint.
- Přidávání ovládacích prvků ASP.NET do stránky aplikace.
- Přidání kódu za ovládací prvky ASP.NET
- Testování stránky aplikace.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

- Podporované edice Windows a SharePointu.

## <a name="create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint

Nejprve vytvořte **prázdný projekt služby SharePoint**. Později přidáte položku **stránky aplikace** do tohoto projektu.

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Otevřete dialogové okno **Nový projekt** , rozbalte uzel **Office/SharePoint** v jazyce, který chcete použít, a pak zvolte uzel **řešení služby SharePoint** .

3. V podokně **Nainstalované šablony sady Visual Studio** vyberte šablonu **projektu SharePoint 2010 – prázdná** . Pojmenujte projekt **MySharePointProject**a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** . Tento průvodce umožňuje vybrat lokalitu, kterou budete používat k ladění projektu a úroveň důvěryhodnosti řešení.

4. Zvolte možnost **nasadit jako řešení farmy** a potom kliknutím na tlačítko **Dokončit** přijměte výchozí místní web služby SharePoint.

## <a name="create-an-application-page"></a>Vytvoření stránky aplikace

Chcete-li vytvořit stránku aplikace, přidejte do projektu položku **stránky aplikace** .

1. V **Průzkumník řešení**vyberte projekt **MySharePointProject** .

2. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte **stránku aplikace (jenom šablona řešení farmy** ).

4. Pojmenujte stránku **SearchItems**a pak klikněte na tlačítko **Přidat** .

     Návrhář Visual Web Developer zobrazí stránku aplikace ve **zdrojovém** zobrazení, kde vidíte prvky HTML stránky. Návrhář zobrazí značky pro několik ovládacích prvků <xref:System.Web.UI.WebControls.Content>. Každý ovládací prvek se mapuje na ovládací prvek <xref:System.Web.UI.WebControls.ContentPlaceHolder>, který je definován na výchozí stránce předlohy aplikací.

## <a name="design-the-layout-of-the-application-page"></a>Návrh rozložení stránky aplikace

Položka stránky aplikace umožňuje použít návrháře k přidání ovládacích prvků ASP.NET do stránky aplikace. Tento návrhář je stejný Návrhář, který se používá v aplikaci Visual Web Developer. Přidejte popisek, seznam přepínačů a tabulku do zobrazení **zdroje** návrháře a pak nastavte vlastnosti stejným způsobem jako při návrhu libovolné standardní stránky ASP.NET.

1. Na panelu nabídek vyberte možnost **zobrazit** > **Sada nástrojů**.

2. V uzlu standardní v **sadě nástrojů**proveďte jeden z následujících kroků:

    - Otevřete místní nabídku položky **popisek** , zvolte možnost **Kopírovat**, otevřete místní nabídku pro řádek pod ovládacím prvkem obsahu **PlaceHolderMain** v návrháři a pak zvolte možnost **Vložit**.

    - Přetáhněte položku **popisek** z **panelu nástrojů** na tělo ovládacího prvku obsahu **PlaceHolderMain** .

3. Opakujte předchozí krok a přidejte položku **DropDownList** a položku **tabulky** do ovládacího prvku obsahu **PlaceHolderMain** .

4. V Návrháři změňte hodnotu atributu `Text` ovládacího prvku popisek tak, aby **zobrazoval všechny položky**.

5. V Návrháři nahraďte prvek `<asp:DropDownList>` následujícím kódem XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Zpracování událostí ovládacích prvků na stránce

Ovládání ovládacích prvků na stránce aplikace stejně jako jakékoli ASP.NET stránky. V tomto postupu zpracujete událost `SelectedIndexChanged` rozevíracího seznamu.

1. V nabídce **zobrazení** vyberte položku **kód**.

     V editoru kódu se otevře soubor kódu stránky aplikace.

2. Přidejte následující metodu do třídy `SearchItems`. Tento kód zpracovává událost <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> <xref:System.Web.UI.WebControls.DropDownList> voláním metody, kterou vytvoříte později v tomto návodu.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Do horní části souboru kódu stránky aplikace přidejte následující příkazy.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Přidejte následující metodu do třídy `SearchItems`. Tato metoda projde všechny lokality na serverové farmě a vyhledá položky vytvořené nebo upravené aktuálním uživatelem.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Přidejte následující metodu do třídy `SearchItems`. Tato metoda zobrazí položky vytvořené nebo upravené aktuálním uživatelem v tabulce.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testování stránky aplikace

Při spuštění projektu se otevře web služby SharePoint a zobrazí se stránka aplikace.

1. V **Průzkumník řešení**otevřete místní nabídku stránky aplikace a zvolte možnost **nastavit jako položku po spuštění**.

2. Klikněte na klávesu **F5** .

     Otevře se web služby SharePoint.

3. Na stránce aplikace vyberte možnost **upraveno mnou** .

     Stránka aplikace se aktualizuje a zobrazí všechny položky, které jste upravili ve všech webech na serverové farmě.

4. Na stránce aplikace vyberte v seznamu možnost **Vytvořeno uživatelem** .

     Stránka aplikace se aktualizuje a zobrazí všechny položky, které jste vytvořili ve všech webech na serverové farmě.

## <a name="next-steps"></a>Další kroky

Další informace o stránkách aplikace SharePoint naleznete v tématu [Vytvoření stránek aplikace pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Další informace o návrhu obsahu stránky SharePointu pomocí vizuálního webového návrháře najdete v těchto tématech:

- [Vytvořte webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Viz také:

[Postupy: Vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)
[_layouts typu stránky](/previous-versions/office/aa979604(v=office.14)) aplikace
