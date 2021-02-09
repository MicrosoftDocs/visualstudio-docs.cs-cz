---
title: 'Postupy: Přidání položky místní nabídky do projektů služby SharePoint | Microsoft Docs'
titleSuffix: ''
description: Přidat položku místní nabídky do projektu služby SharePoint v aplikaci Visual Studio. Položka nabídky se zobrazí po kliknutí pravým tlačítkem myši na uzel projektu v Průzkumník řešení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4244fb83d4792786baeb99693dc0fee04624d37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882723"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Postupy: Přidání položky místní nabídky do projektů služby SharePoint
  Můžete přidat položku místní nabídky do libovolného projektu služby SharePoint. Položka nabídky se zobrazí, když uživatel klikne pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**.

 Následující postup předpokládá, že jste již vytvořili rozšíření projektu. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Přidání položky místní nabídky do projektů služby SharePoint

1. V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodě vaší <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementace zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> událost parametru *ProjectService* .

2. V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> událost přidejte nový <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objekt do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> kolekce nebo v <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> parametru argumenty události.

3. V <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> obslužné rutině události pro nový <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objekt proveďte úkoly, které chcete spustit, když uživatel klikne na položku místní nabídky.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat položku místní nabídky do uzlů projektu služby SharePoint v **Průzkumník řešení**. Když uživatel klikne pravým tlačítkem myši na uzel projektu a klikne na položku nabídky **napsat zprávu pro okno výstup** , Visual Studio zobrazí zprávu v okně **výstup** . Tento příklad používá službu projektu SharePoint k zobrazení zprávy. Další informace naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje projekt knihovny tříd s odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
