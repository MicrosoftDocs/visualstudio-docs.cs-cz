---
title: Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru | Microsoft Docs
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
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7211d31b8e57a88d3f6a5a585e912dd267cf943
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325583"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru
  V sadě Visual Studio, můžete připojení na místní weby služby SharePoint na vývojovém počítači pomocí **připojení služby SharePoint** uzel v **Průzkumníka serveru** okno. Tento uzel zobrazuje mnoho součásti místních webů služby SharePoint v hierarchickém stromovém zobrazení. Můžete například zobrazit seznamy, knihovny dokumentů a typy obsahu na místních serverech. Další informace o používání **Průzkumníka serveru** Pokud chcete připojit k místní weby služby SharePoint, najdete v části [připojení Procházet služby SharePoint pomocí Průzkumníka serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Můžete rozšířit **připojení služby SharePoint** uzlu vytváření rozšíření pro existující uzly, nebo vytvořením vlastního typu uzlu a její přidání do hierarchie uzlů.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Úlohy pro rozšíření uzlu připojení služby SharePoint
 Chcete-li rozšířit stávající uzel, vytvořte rozšíření sady Visual Studio, který implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Když rozšíříte uzlem, můžete přidat funkce na uzlu jako vlastní položky místní nabídky nebo vlastní vlastnosti. Další informace najdete v tématu [postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Chcete-li vytvořit vlastní typ uzlu, vytvořte rozšíření sady Visual Studio, který implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Vytvořit vlastní uzel, pokud chcete zobrazit součásti webů služby SharePoint, které nejsou zobrazeny v **Průzkumníka serveru** ve výchozím nastavení. Například **Průzkumníka serveru** nemá zobrazení galerii webových částí webu služby SharePoint ve výchozím nastavení, ale můžete přidat vlastní uzel, který to. Další informace najdete v tématu [postupy: Přidání vlastního uzlu služby SharePoint do Průzkumníka serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) a [návod: rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="add-custom-properties-to-nodes"></a>Přidání vlastních vlastností do uzlů
 Když rozšíření uzlu nebo vytvořit vlastní typ uzlu, můžete do uzlu přidat vlastní vlastnosti. Vlastnosti se zobrazí v **vlastnosti** okno, pokud je vybrán uzel.  
  
 Existují dva typy vlastní vlastnosti, které můžete přidat do uzlu:  
  
-   Vlastnosti, které zobrazují sadu jen pro čtení dat z webu služby SharePoint. Data popisuje součást služby SharePoint, která představuje uzel. Návod, jak to udělat najdete v tématu [návod: rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Vlastnosti, které zobrazují data vlastní pro čtení a zápis. Příklad kódu, který ukazuje, jak to udělat, najdete v části [postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="get-data-for-built-in-nodes"></a>Získání dat pro předdefinovaný uzly
 Všechny předdefinované uzly poskytované sadě Visual Studio obsahují některá data o součást služby SharePoint, které představují. Například uzel, který představuje seznam na webu služby SharePoint poskytuje některá data o seznamu, jako je název a adresu URL výchozí zobrazení seznamu.  
  
 Pro přístup k těmto datům, načíst objekt dat z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objekt, který představuje uzel vás zajímá. Typ objektu dat závisí na typu uzlu.  
  
 Následující příklad kódu ukazuje, jak získat objekt dat pro seznam uzlů. Tady je příklad v rámci většího příkladu najdete v sekci [postupy: získání dat pro předdefinovaný uzel služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Následující tabulka uvádí typy objektů dat pro každý typ předdefinovaný uzel.  
  
|Typ uzlu|Datový typ objektu|  
|---------------|----------------------|  
|Uzel serveru SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Typ obsahu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Funkce|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Pole|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Seznam|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Seznam šablony|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Zobrazení seznamu (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Přidružení pracovního postupu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Pracovní postup šablony|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Další informace o používání <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost, najdete v části [rozšíření nástrojů přidružení vlastních dat se službou SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Viz také:
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumníka serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Postupy: získání dat pro předdefinovaný uzel služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Přidružení vlastních dat k rozšíření nástrojů SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Procházení připojení služby SharePoint pomocí Průzkumníka serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  
