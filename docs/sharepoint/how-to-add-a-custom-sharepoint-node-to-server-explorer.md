---
title: 'Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru | Microsoft Docs'
titleSuffix: ''
description: Přidejte vlastní uzel služby SharePoint pro Průzkumník serveru v aplikaci Visual Studio. Zobrazí další komponenty SharePointu, které se ve výchozím nastavení nezobrazují ve Průzkumník serveru.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be772075be27cc8d6e58b6b54bb281a127f4677f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878120"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru
  Do uzlu **připojení služby SharePoint** v **Průzkumník serveru** můžete přidat vlastní uzly. To je užitečné, když chcete zobrazit další komponenty SharePointu, které se ve výchozím nastavení nezobrazují ve **Průzkumník serveru** . Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Chcete-li přidat vlastní uzel, nejprve vytvořte třídu, která definuje nový uzel. Pak vytvořte rozšíření, které přidá uzel jako podřízenou položku existujícího uzlu.

### <a name="to-define-the-new-node"></a>Definování nového uzlu

1. Vytvořte projekt knihovny tříd.

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. složení

    - System. Drawing

3. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní.

4. Do třídy přidejte následující atributy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Tento atribut umožňuje aplikaci Visual Studio vyhledat a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> typ konstruktoru atributu.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. V definici uzlu tento atribut určuje identifikátor řetězce pro nový uzel. Doporučujeme použít formát *název společnosti*. *název uzlu* , aby se zajistilo, že všechny uzly mají jedinečný identifikátor.

5. V implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metody použijte k nakonfigurování chování nového uzlu členy parametru *typeDefinition* . Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objekt, který poskytuje přístup k událostem definovaným v <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> rozhraní.

     Následující příklad kódu ukazuje, jak definovat nový uzel. V tomto příkladu se předpokládá, že projekt obsahuje ikonu s názvem CustomChildNodeIcon jako vložený prostředek.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Přidání nového uzlu jako podřízeného existujícího uzlu

1. Ve stejném projektu jako definice uzlu vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní.

2. Přidejte <xref:System.ComponentModel.Composition.ExportAttribute> atribut do třídy. Tento atribut umožňuje aplikaci Visual Studio vyhledat a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typ konstruktoru atributu.

3. Přidejte <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atribut do třídy. V rozšíření uzlu tento atribut určuje identifikátor řetězce pro typ uzlu, který chcete rozšířit.

     Chcete-li určit předdefinované typy uzlů poskytované aplikací Visual Studio, předejte jednu z následujících hodnot výčtu konstruktoru atributu:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Tyto hodnoty použijte k určení uzlů připojení lokality (uzly, které zobrazují adresy URL webu), uzlů webu nebo všech ostatních nadřazených uzlů v **Průzkumník serveru**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Pomocí těchto hodnot můžete zadat jeden z vestavěných uzlů, které představují jednotlivé komponenty na webu služby SharePoint, jako je například uzel, který představuje seznam, pole nebo typ obsahu.

4. V implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody zpracujte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> událost <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametru.

5. V <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> obslužné rutině události přidejte nový uzel do kolekce podřízených uzlů <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objektu, který je vystavený parametrem argumenty události.

     Následující příklad kódu ukazuje, jak přidat nový uzel jako podřízený uzel webu služby SharePoint v **Průzkumník serveru**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Kompletní příklad
 Následující příklad kódu poskytuje kompletní kód pro definování jednoduchého uzlu a jeho přidání jako podřízený uzel webu služby SharePoint v **Průzkumník serveru**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Zkompilování kódu
 V tomto příkladu se předpokládá, že projekt obsahuje ikonu s názvem CustomChildNodeIcon jako vložený prostředek. Tento příklad také vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

- System. Drawing

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření **Průzkumník serveru** , vytvořte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Postupy: rozšiřování uzlu služby SharePoint v Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
