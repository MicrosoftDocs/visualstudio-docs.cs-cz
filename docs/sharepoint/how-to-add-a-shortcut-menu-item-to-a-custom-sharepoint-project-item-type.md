---
title: Přidat položku místní nabídky do vlastního typu položky projektu služby SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39de735c09c97541684628c8e4140aa42d119500
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585872"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Postupy: Přidání položky místní nabídky do vlastního typu položky projektu služby SharePoint
  Při definování vlastního typu položky projektu služby SharePoint lze přidat položku místní nabídky do položky projektu. Položka nabídky se zobrazí, když uživatel klikne pravým tlačítkem myši na položku projektu v **Průzkumník řešení**.

 Následující postup předpokládá, že jste již definovali vlastní typ položky projektu služby SharePoint. Další informace naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Přidání položky místní nabídky do vlastního typu položky projektu

1. V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodě vaší <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementace zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> událost parametru *ProjectItemTypeDefinition* .

2. V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> událost přidejte nový <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objekt do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> kolekce nebo v <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> parametru argumenty události.

3. V <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> obslužné rutině události pro nový <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objekt proveďte úkoly, které chcete spustit, když uživatel zvolí položku místní nabídky.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat položku kontextové nabídky do vlastního typu položky projektu. Když uživatel otevře místní nabídku z položky projektu v **Průzkumník řešení** a zvolí položku nabídky **napsat zprávu pro okno výstup** , Visual Studio zobrazí zprávu v okně **výstup** .

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Tento příklad používá službu projektu SharePoint k zápisu zprávy do okna **výstup** . Další informace naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje projekt knihovny tříd s odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-project-item"></a>Nasazení položky projektu
 Chcete-li povolit jiným vývojářům používat položku projektu, vytvořte šablonu projektu nebo šablonu položky projektu. Další informace naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Chcete-li nasadit položku projektu, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení, šablonu a všechny další soubory, které chcete distribuovat s položkou projektu. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
