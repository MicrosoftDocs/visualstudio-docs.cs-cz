---
title: 'Postupy: rozšiřování uzlu služby SharePoint v Průzkumník serveru | Microsoft Docs'
description: Seznamte se s postupem rozšiřování uzlu služby SharePoint v Průzkumník serveru pomocí uzlu připojení služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e38f1d18736c18f5273eb2e202de52af81e73f85
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217447"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Postupy: rozšiřování uzlu služby SharePoint v Průzkumník serveru
  Uzly můžete v uzlu **připojení služby SharePoint** v **Průzkumník serveru** zvětšit. To je užitečné, když chcete přidat nové podřízené uzly, položky místní nabídky nebo vlastnosti do existujícího uzlu. Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Postup při rozšiřování uzlu služby SharePoint v Průzkumník serveru

1. Vytvořte projekt knihovny tříd.

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. složení

3. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní.

4. Přidejte <xref:System.ComponentModel.Composition.ExportAttribute> atribut do třídy. Tento atribut umožňuje aplikaci Visual Studio vyhledat a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typ konstruktoru atributu.

5. Přidejte <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atribut do třídy. Tento atribut určuje identifikátor řetězce pro typ uzlu, který chcete zvětšit.

     Chcete-li určit předdefinované typy uzlů poskytované aplikací Visual Studio, předejte jednu z následujících hodnot výčtu konstruktoru atributu:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Tyto hodnoty použijte k určení uzlů připojení lokality (uzly, které zobrazují adresy URL webu), uzlů webu nebo všech ostatních nadřazených uzlů v **Průzkumník serveru**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Pomocí těchto hodnot můžete zadat jeden z vestavěných uzlů, které představují jednotlivé komponenty na webu služby SharePoint, jako je například uzel, který představuje seznam, pole nebo typ obsahu.

6. V implementaci <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody pomocí členů parametru *NodeType* přidejte do uzlu funkce. Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objekt, který poskytuje přístup k událostem definovaným v <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> rozhraní. Například můžete zpracovat následující události:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Zpracujte tuto událost pro přidání nových podřízených uzlů do uzlu. Další informace najdete v tématu [Postup: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Zpracujte tuto událost, pokud chcete přidat vlastní položku místní nabídky do uzlu.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Zpracujte tuto událost pro přidání vlastních vlastností do uzlu. Vlastnosti se zobrazí v okně **vlastnosti** , když je vybrán uzel.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak vytvořit dva různé typy rozšíření uzlu:

- Rozšíření, které přidá položku kontextové nabídky do uzlů webu služby SharePoint. Po kliknutí na položku nabídky se zobrazí název uzlu, na který jste klikli.

- Rozšíření, které přidá vlastní vlastnost s názvem **ContosoExampleProperty** , do každého uzlu, který představuje pole s názvem **text**.

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  Toto rozšíření přidá do uzlů upravitelnou vlastnost řetězce. Můžete také vytvořit vlastní vlastnosti, které zobrazují data jen pro čtení ze serveru SharePoint. Příklad, který ukazuje, jak to provést, naleznete v tématu [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. složení

- System. Windows. Forms

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření **Průzkumník serveru** , vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Postupy: Přidání vlastního uzlu služby SharePoint do Průzkumník serveru](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Přidružit vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
