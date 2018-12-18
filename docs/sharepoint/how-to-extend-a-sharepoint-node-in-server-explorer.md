---
title: 'Postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f61afe90ed48064c79dd40c0c0975155c956e3e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861836"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru
  Uzly v rámci můžete rozšířit **připojení služby SharePoint** uzel v **Průzkumníka serveru**. To je užitečné, pokud chcete přidat nové podřízené uzly, položky místní nabídky nebo vlastnosti pro existující uzel. Další informace najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Rozšíření uzlu služby SharePoint v Průzkumníku serveru  
  
1.  Vytvořte projekt knihovny tříd.  
  
2.  Přidejte odkazy na následující sestavení:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní.  
  
4.  Přidat <xref:System.ComponentModel.Composition.ExportAttribute> atribut třídy. Tento atribut umožňuje sadě Visual Studio zjišťovat a načíst vaše <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementace. Předat <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typ konstruktoru atributu.  
  
5.  Přidat <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atribut třídy. Tento atribut určuje identifikátor řetězce pro typ uzlu, který chcete rozšířit.  
  
     Určení typů integrované uzlem poskytovaný sadou Visual Studio, předejte jeden z následujících hodnot výčtu konstruktoru atributu:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Použijte tyto hodnoty zadat uzlů připojení lokality (uzly, které zobrazují adresy URL), lokality uzly nebo všechny ostatní nadřazené uzly v **Průzkumníka serveru**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Použijte tyto hodnoty zadat jeden z předdefinovaných uzlů, které představují jednotlivé součásti na Sharepointovém webu, jako je například uzel, který představuje seznam, pole nebo typ obsahu.  
  
6.  Ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody, použijte členy *nodeType* parametru se přidá funkce do uzlu. Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objekt, který poskytuje přístup k události definované v <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> rozhraní. Můžete například zpracovávat následující události:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Zpracování této události pro přidání nové podřízené uzly uzlu. Další informace najdete v tématu [postupy: Přidání vlastního uzlu služby SharePoint do Průzkumníka serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Zpracování této události pro přidání položky vlastní místní nabídky k uzlu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Zpracování této události k přidání vlastních vlastností do uzlu. Vlastnosti se zobrazí v **vlastnosti** okno při výběru uzlu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit dva různé typy rozšíření uzlu:  
  
- Rozšíření, které se přidá položka kontextové nabídky do uzlů serveru SharePoint. Po kliknutí na položku nabídky, zobrazí název, který došlo ke kliknutí na uzel.  
  
- Rozšíření, které přidá vlastní vlastnost s názvem **ContosoExampleProperty** na každém uzlu, který představuje pole s názvem **tělo**.  
  
  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
  Toto rozšíření přidá vlastnost upravit řetězec do uzlů. Můžete také vytvořit vlastní vlastnosti, které zobrazují jen pro čtení dat ze serveru SharePoint. Příklad, který ukazuje, jak to provést, najdete v části [návod: rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje odkazy na následující sestavení:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>Nasazení rozšíření  
 K nasazení **Průzkumníka serveru** rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) balíčku pro sestavení a všechny další soubory, které chcete distribuovat s příponou. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumníka serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Přidružení vlastních dat k rozšíření nástrojů SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
