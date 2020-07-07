---
title: 'Návod: Vytvoření základního projektu definice webu | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c06f4df5d1efe06ad2537bd2e65f2c239f3be2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016769"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Návod: Vytvoření základního projektu definice webu
  V tomto návodu se dozvíte, jak vytvořit základní definici webu obsahující vizuální webovou část s některými ovládacími prvky. Z důvodu srozumitelnosti má vizuální webová část, kterou vytvoříte, pouze několik ovládacích prvků. Můžete ale vytvořit pokročilejší definice webů SharePointu, které budou zahrnovat víc funkcí.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření definice webu pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] šablony projektu.

- Vytvoření webu služby SharePoint pomocí definice webu ve službě SharePoint.

- Přidání vizuální webové části do řešení.

- Přizpůsobení stránky default. aspx webu přidáním nové vizuální webové části do této stránky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Microsoft Windows a SharePointu. Další informace najdete v tématu požadavky pro vývoj řešení služby SharePoint.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Vytvoření řešení definice webu
 Nejprve vytvořte projekt definice webu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Vytvoření projektu definice webu

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. Pokud je vaše rozhraní IDE nastaveno na použití Visual Basic vývojové nastavení, na panelu nabídky vyberte **soubor**  >  **Nový projekt**.

    Zobrazí se dialogové okno **Nový projekt**.

2. Rozbalte uzel **Visual C#** nebo uzel **Visual Basic** , rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V seznamu **šablony** vyberte šablonu **projektu SharePoint 2010** .

4. Do pole **název** zadejte **TestSiteDef**a poté klikněte na tlačítko **OK** .

    Zobrazí se **Průvodce přizpůsobením SharePointu** .

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL webu služby SharePoint, kam chcete ladit definici webu, nebo použijte výchozí umístění (http://<em>System Name</em>/).

6. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** vyberte možnost **nasadit jako řešení farmy** .

    Všechny projekty definice webu musí být nasazeny jako řešení farmy. Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. Klikněte na tlačítko **Dokončit** .

    Projekt se zobrazí v **Průzkumník řešení**.

8. V **Průzkumník řešení**zvolte uzel projektu a potom v řádku nabídek zvolte **projekt**  >  **Přidat novou položku**.

9. V části **Visual C#** nebo **Visual Basic**rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

10. V podokně **šablony** zvolte šablonu **definice webu** , ponechte **název** jako **SiteDefinition1**a pak klikněte na tlačítko **Přidat** .

## <a name="create-a-visual-web-part"></a>Vytvoření vizuální webové části
 Dále vytvořte vizuální webovou část, která se zobrazí na hlavní stránce definice webu.

#### <a name="to-create-a-visual-web-part"></a>Vytvoření vizuální webové části

1. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .

2. Zvolte uzel projektu **SiteDefinition1** a potom v řádku nabídek zvolte **projekt**  >  **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku**.

3. Rozbalte uzel **Visual C#** nebo uzel **Visual Basic** , rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V seznamu šablon vyberte šablonu **Visual Web Part** , ponechte výchozí název VisualWebPart1 a pak klikněte na tlačítko **Přidat** .

     Otevře se soubor *VisualWebPart1. ascx* .

5. V dolní části *VisualWebPart1. ascx*přidejte následující kód, který přidá tři ovládací prvky do formuláře: textové pole, tlačítko a popisek:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. V části *VisualWebPart1. ascx*otevřete soubor *VisualWebPart1.ascx.cs* (pro [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) nebo *VisualWebPart1. ascx. vb* (pro [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) a přidejte následující kód:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Tento kód přidá funkce pro kliknutí na tlačítko webové části.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Přidání vizuální webové části na výchozí stránku ASPX
 Dále přidejte vizuální webovou část na výchozí stránku ASPX definice webu.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Přidání vizuální webové části na výchozí stránku ASPX

1. Otevřete stránku Default. aspx a přidejte následující řádek pod `WebPartPages` značku:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Tento řádek přidruží název MyWebPartControls k webové části a kódu. Parametr *Namespace* odpovídá oboru názvů, který se používá v souboru kódu *VisualWebPart1. ascx* .

2. Po `</asp:Content>` elementu nahraďte celý `ContentPlaceHolderId="PlaceHolderMain"` oddíl a jeho obsah následujícím kódem:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Tento kód vytvoří odkaz na vizuální webovou část, kterou jste vytvořili dříve.

3. V **Průzkumník řešení**otevřete místní nabídku uzlu **SiteDefinition1** a pak zvolte **nastavit jako položku po spuštění**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Nasazení a spuštění řešení definice webu
 Dále nasaďte projekt do služby SharePoint a poté spusťte projekt.

#### <a name="to-deploy-and-run-the-site-definition"></a>Nasazení a spuštění definice webu

- Na panelu nabídek vyberte **sestavení**  >  **nasadit TestSiteDef**.

- Klikněte na klávesu **F5** .

     Visual Studio zkompiluje kód, přidá jeho funkce, zabalí všechny soubory do souboru řešení služby SharePoint (WSP) a nasadí soubor WSP na server SharePoint. SharePoint potom nainstaluje soubory a pak tyto funkce aktivuje.

## <a name="create-a-site-based-on-the-site-definition"></a>Vytvoření webu na základě definice webu
 Dále vytvořte web pomocí definice nové lokality.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Vytvoření webu s použitím definice webu

1. Na webu služby SharePoint se zobrazí stránka nový web SharePointu.

2. V části **název a popis** zadejte **Moje nové pracoviště** pro název a popis webu.

3. V části **adresa** webu zadejte **mynewsite** do pole **název adresy URL** .

4. V části **Šablona** vyberte kartu **přizpůsobení SharePointu** .

5. V seznamu **Vyberte šablonu** zvolte možnost **SiteDefinition1**.

6. U ostatních nastavení ponechte výchozí hodnoty a pak klikněte na tlačítko **vytvořit** .

     Zobrazí se nový web.

## <a name="test-the-new-site"></a>Testování nového webu
 V dalším kroku otestujte novou lokalitu a ověřte, jestli funguje správně.

#### <a name="to-test-the-new-site"></a>Otestování nového webu

- Na výchozí stránce ASPX zadejte nějaký text a pak klikněte na tlačítko **změnit text popisku** vedle textového pole.

     Text se zobrazí v popisku na pravé straně tlačítka.

## <a name="see-also"></a>Viz také:
- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
