---
title: 'Návod: Vytvoření základního projektu definice webu | Dokumentace Microsoftu'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a9a879db7c1d24dbfd8312dbc75d9b0bbaa8803
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844404"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Návod: Vytvoření základního projektu definice webu
  Tento návod ukazuje, jak vytvořit základní definici webu obsahující vizuální webovou část s některými ovládacími prvky na něj. Vizuální webové části, který vytvoříte přehlednosti má několik ovládacích prvků. Můžete však vytvořit složitější definic webu služby SharePoint, které zahrnují další funkce.  
  
 Tento návod demonstruje následující úkoly:  
  
- Vytvoření s použitím definice webu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] šablony projektu.  
  
- Vytvoření webu služby SharePoint s použitím definice webu ve službě SharePoint.  
  
- Přidání vizuální webové části do řešení.  
  
- Přizpůsobení stránku default.aspx přidáním nové vizuální webové části.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované vydání systému Microsoft Windows a SharePoint. Další informace najdete v tématu požadavky na vývoj řešení služby SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-site-definition-solution"></a>Vytvoření řešení definice webu
 Vytvoření projektu definice webu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Vytvoření projektu definice webu  
  
1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**. Pokud vaše rozhraní IDE nastaveno pro použití vývojového nastavení jazyka Visual Basic, v řádku nabídek, zvolte **souboru** > **nový projekt**.  
  
    **Nový projekt** zobrazí se dialogové okno.  
  
2. Rozbalte **Visual C#**  uzlu nebo **jazyka Visual Basic** uzlu, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
3. V **šablony** klikněte na položku **projektu služby SharePoint 2010** šablony.  
  
4. V **název** zadejte **TestSiteDef**a klikněte na tlačítko **OK** tlačítko.  
  
    **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
5. Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte adresu URL pro web služby SharePoint, ve kterém chcete ladit definice webu nebo použijte výchozí umístění (http://<em>systémový název</em>/).  
  
6. V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** zvolte **nasadit jako řešení farmy** přepínač.  
  
    Všechny projekty definic webů se musí nasadit jako řešení farmy. Další informace o řešení v izolovaném prostoru a řešení farmy najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Zvolte **Dokončit** tlačítko.  
  
    Projekt se objeví v **Průzkumníka řešení**.  
  
8. V **Průzkumníka řešení**, zvolte uzel projektu a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.  
  
9. V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
10. V **šablony** podokně, vyberte **definice webu** šablony, ponechejte tuto položku **název** jako **SiteDefinition1**a klikněte na tlačítko  **Přidat** tlačítko.  
  
## <a name="create-a-visual-web-part"></a>Vytvoření vizuální webové části
 V dalším kroku vytvoření vizuální webové části, aby se zobrazovaly na hlavní stránku definice webu.  
  
#### <a name="to-create-a-visual-web-part"></a>Chcete-li vytvořit vizuální webové části
  
1.  V **Průzkumníka řešení**, zvolte **zobrazit všechny soubory** tlačítko.  
  
2.  Zvolte **SiteDefinition1** uzel projektu a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
3.  Rozbalte **Visual C#**  uzlu nebo **jazyka Visual Basic** uzlu, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
4.  V seznamu šablon vyberte **vizuální webové části** šablony, ponechat výchozí název VisualWebPart1 a klikněte na tlačítko **přidat** tlačítko.  
  
     *VisualWebPart1.ascx* soubor otevře.  
  
5.  V dolní části *VisualWebPart1.ascx*, přidejte následující kód k přidejte tři ovládací prvky do formuláře: textové pole, tlačítko a popisek:  
  
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
  
6.  V části *VisualWebPart1.ascx*, otevřete *VisualWebPart1.ascx.cs* souboru (pro [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) nebo *VisualWebPart1.ascx.vb* (pro [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) a pak přidejte Následující kód:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Tento kód přidá funkce pro webové části na tlačítko.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Přidání vizuální webové části na výchozí stránku ASPX
 V dalším kroku přidáte vizuální webové části na výchozí stránku ASPX definice webu.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Přidání vizuální webové části na výchozí stránku ASPX
  
1.  Otevřete stránku default.aspx a poté přidejte následující řádek pod `WebPartPages` značky:  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Tento řádek přiřadí název MyWebPartControls webové části a jeho kód. *Namespace* parametr shoduje se obor názvů, který je používán *VisualWebPart1.ascx* soubor kódu.  
  
2.  Po `</asp:Content>` elementu, nahraďte celý `ContentPlaceHolderId="PlaceHolderMain"` oddílu a jeho obsah následujícím kódem:  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Tento kód vytvoří odkaz na vizuální webové části, který jste vytvořili dříve.  
  
3.  V **Průzkumníka řešení**, otevřete místní nabídku **SiteDefinition1** uzel a klikněte na tlačítko **nastavit jako položku při spuštění**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Nasazení a spuštění řešení definice webu
 V dalším kroku nasaďte projekt do služby SharePoint a spusťte projekt.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Nasazení a spuštění definice webu  
  
-   V panelu nabídky zvolte **sestavení** > **nasazení TestSiteDef**.  
  
-   Zvolte **F5** klíč.  
  
     Visual Studio kompiluje kód, přidá jeho funkce, všechny soubory balíčků do souboru řešení (soubor WSP) pro SharePoint a nasadí soubor WSP na SharePoint Server. SharePoint pak nainstaluje soubory a potom aktivuje funkce.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Vytvoření webu na základě definice webu
 V dalším kroku vytvoření webu s použitím nové definice webu.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Vytvoření webu s použitím definice webu  
  
1.  Na webu služby SharePoint se zobrazí stránka Nový web Sharepointu.  
  
2.  V **nadpis a popis** části, zadejte **Moje nové lokality** název a popis lokality.  
  
3.  V **adresa webu** části, zadejte **Nový_server** v **název adresy URL** pole.  
  
4.  V **šablony** zvolte **přizpůsobení Sharepointu** kartu.  
  
5.  V **vyberte šablonu** klikněte na položku **SiteDefinition1**.  
  
6.  Ostatní nastavení ponechte jejich výchozí hodnoty a klikněte na tlačítko **vytvořit** tlačítko.  
  
     Zobrazí se nový web.  
  
## <a name="test-the-new-site"></a>Otestování nového webu
 V dalším kroku otestujte nové lokality k ověření, zda funguje správně.  
  
#### <a name="to-test-the-new-site"></a>Otestování nového webu  
  
-   Na výchozí stránku ASPX, zadejte nějaký text a klikněte na tlačítko **změnit Text popisku** tlačítko vedle textového pole.  
  
     Text se zobrazí v popisku na pravé straně tlačítka.  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
