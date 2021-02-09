---
title: Rozšíření uzlu připojení služby SharePoint v Průzkumník serveru | Microsoft Docs
titleSuffix: ''
description: Rozšíří uzel připojení služby SharePoint v okně Průzkumník serveru v aplikaci Visual Studio. Přidejte do uzlů vlastní vlastnosti. Získat data pro předdefinované uzly.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c10c2bc69086e3c98633ba746c1e6fc8d7f2a20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889691"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozšíří uzel připojení služby SharePoint v Průzkumník serveru
  V aplikaci Visual Studio se můžete připojit k místním webům služby SharePoint ve vývojovém počítači pomocí uzlu **připojení služby SharePoint** v okně **Průzkumník serveru** . Tento uzel zobrazuje spoustu součástí místních webů SharePointu v hierarchickém stromovém zobrazení. Můžete například zobrazit seznamy, knihovny dokumentů a typy obsahu v místních lokalitách. Další informace o použití **Průzkumník serveru** pro připojení k místním webům služby SharePoint naleznete v tématu [procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Uzel **připojení služby SharePoint** můžete roztáhnout vytvořením rozšíření pro existující uzly nebo vytvořením vlastního typu uzlu a jeho přidáním do hierarchie uzlů.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Úlohy pro rozšíření uzlu připojení služby SharePoint
 Chcete-li rozšířit existující uzel, vytvořte rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Když rozšíříte uzel, můžete do uzlu přidat funkce, jako jsou například vlastní položky místní nabídky nebo vlastní vlastnosti. Další informace najdete v tématu [Postup: rozšiřování uzlu služby SharePoint v Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Chcete-li vytvořit vlastní typ uzlu, vytvořte rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Pokud chcete zobrazit součásti webů SharePointu, které se ve výchozím nastavení nezobrazuje ve **Průzkumník serveru** , vytvořte vlastní uzel. Například **Průzkumník serveru** nezobrazuje galerii webových částí webu služby SharePoint ve výchozím nastavení, ale můžete přidat vlastní uzel, který to dělá. Další informace najdete v tématu [Postup: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) a [Návod: roztažení Průzkumník serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Přidání vlastních vlastností do uzlů
 Když rozšíříte uzel nebo vytvoříte vlastní typ uzlu, můžete do uzlu přidat vlastní vlastnosti. Vlastnosti se zobrazí v okně **vlastnosti** , když je vybrán uzel.

 Existují dva typy vlastních vlastností, které můžete přidat do uzlu:

- Vlastnosti, které zobrazují sadu dat jen pro čtení z webu služby SharePoint. Data popisují komponentu služby SharePoint, kterou uzel představuje. Návod, který ukazuje, jak to provést, naleznete v tématu [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Vlastnosti, které zobrazují vlastní data pro čtení a zápis. Příklad kódu, který ukazuje, jak to provést, naleznete v tématu [How to: extend a Node SharePoint in Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Získat data pro předdefinované uzly
 Všechny integrované uzly, které poskytuje Visual Studio, obsahují data o komponentě SharePointu, kterou představují. Například uzel, který představuje seznam na webu služby SharePoint, obsahuje data o seznamu, jako je například název a adresa URL výchozího zobrazení seznamu.

 Pro přístup k těmto datům Načtěte datový objekt z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objektu, který představuje uzel, který vás zajímá. Typ datového objektu závisí na typu uzlu.

 Následující příklad kódu ukazuje, jak získat datový objekt pro uzel seznamu. Chcete-li zobrazit tento příklad v kontextu většího příkladu, přečtěte si téma [How to: získat data pro integrovaný uzel služby SharePoint v Průzkumník serveru](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 V následující tabulce jsou uvedeny typy datových objektů pro každý typ předdefinovaného uzlu.

|Typ uzlu|Typ datového objektu|
|---------------|----------------------|
|Uzel webu služby SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Typ obsahu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Funkce|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Pole|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Seznam|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Šablona seznamu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Zobrazení seznamu (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Přidružení pracovního postupu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Šablona pracovního postupu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti naleznete v tématu [přidružte vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Viz také
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Postupy: rozšiřování uzlu služby SharePoint v Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Postupy: získání dat pro předdefinovaný uzel služby SharePoint v Průzkumník serveru](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Přidružit vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
