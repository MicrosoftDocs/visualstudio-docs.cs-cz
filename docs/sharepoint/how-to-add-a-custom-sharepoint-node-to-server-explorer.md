---
title: 'Postupy: Přidání uzlu vlastní služby SharePoint do Průzkumníka serveru | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb0ba7f09ae564a794792ad6f7a60f53f6f6422e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755638"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumníka serveru
  Můžete přidat vlastní uzly v rámci **připojení služby SharePoint** uzlu v **Průzkumníka serveru**. To je užitečné, pokud chcete zobrazit další součásti služby SharePoint, které nejsou zobrazeny v **Průzkumníka serveru** ve výchozím nastavení. Další informace najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Chcete-li přidat vlastní uzel, nejdřív vytvořte třídu, která definuje nový uzel. Pak vytvořte rozšíření, které přidá uzlu jako podřízenou stávající uzel.  
  
### <a name="to-define-the-new-node"></a>Chcete-li definovat nový uzel  
  
1.  Vytvoření projektu knihovny tříd.  
  
2.  Přidejte odkazy na následující sestavení:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní.  
  
4.  Přidejte do třídy následující atributy:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Tento atribut umožňuje sadě Visual Studio zjišťovat a načíst vaše <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementace. Předat <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> typ do konstruktoru atributu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. V definici uzlu tento atribut určuje identifikátor řetězce pro nový uzel. Doporučujeme použít formát *název společnosti*. *Název uzlu* a ujistěte se, že všechny uzly mají jedinečný identifikátor.  
  
5.  V implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metoda, použijte členy *typeDefinition* parametr konfigurace chování nový uzel. Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objekt, který poskytuje přístup k událostí definovaných v <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> rozhraní.  
  
     Následující příklad kódu ukazuje, jak definovat nový uzel. Tento příklad předpokládá, že váš projekt obsahuje ikonu s názvem CustomChildNodeIcon jako vložený prostředek.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Chcete-li přidat nový uzel jako podřízený stávající uzel  
  
1.  Ve stejném projektu jako svou definici. uzel, vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní.  
  
2.  Přidat <xref:System.ComponentModel.Composition.ExportAttribute> atribut třídy. Tento atribut umožňuje sadě Visual Studio zjišťovat a načíst vaše <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementace. Předat <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typ do konstruktoru atributu.  
  
3.  Přidat <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atribut třídy. V uzlu Rozšíření tento atribut určuje identifikátor řetězce pro typ uzlu, který chcete rozšířit.  
  
     Pokud chcete zadat typy předdefinovaný uzel poskytované sadě Visual Studio, předejte jednu z následujících hodnot výčtu konstruktoru atributu:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Použijte tyto hodnoty zadat uzlů připojení lokality (uzly, které zobrazují adresy URL), lokality uzlů nebo všechny ostatní nadřazené uzly v **Průzkumníka serveru**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Použijte tyto hodnoty Pokud chcete zadat jednu z předdefinovaných uzly, které představuje jednotlivou součást na web služby SharePoint, jako je například uzel, který představuje seznam, pole nebo typ obsahu.  
  
4.  V implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metoda, popisovač <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> události <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametr.  
  
5.  V <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> obslužné rutiny události, přidání nového uzlu do kolekce podřízené uzly <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objekt, který je zveřejněný prostřednictvím parametru argumentů události.  
  
     Následující příklad kódu ukazuje, jak přidat nový uzel jako podřízený uzel serveru SharePoint v **Průzkumníka serveru**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Úplný příklad
 Následující příklad kódu obsahuje kompletní kód definovat Jednoduchý uzel a přidat ji jako podřízený uzel serveru SharePoint v **Průzkumníka serveru**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad předpokládá, že váš projekt obsahuje ikonu s názvem CustomChildNodeIcon jako vložený prostředek. Tento příklad vyžaduje také odkazy na následující:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>Nasazení rozšíření  
 K nasazení **Průzkumníka serveru** rozšíření, vytvořte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  
