---
title: Rozšiřování projektů služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967478"
---
# <a name="extend-sharepoint-projects"></a>Rozšiřování projektů SharePoint
  Vytvořte rozšíření projektu, pokud chcete upravit funkce na úrovni projektu v projektech SharePoint. Můžete například přidat vlastní vlastnosti projektu nebo reagovat na události na úrovni projektu, které jsou vyvolány, když uživatel vyvíjí řešení služby SharePoint v aplikaci Visual Studio.

## <a name="create-project-extensions"></a>Vytvořit rozšíření projektu
 Chcete-li rozšířit položku projektu, sestavte sestavení rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Při vytváření rozšíření projektu můžete také přidat následující funkce do projektů služby SharePoint:

- Přidat položku místní nabídky Položka nabídky se zobrazí, když otevřete místní nabídku pro uzel projektu služby SharePoint v **Průzkumník řešení** kliknutím pravým tlačítkem myši na uzel nebo zvolením a následným výběrem klávesy **SHIFT** + **F10** . Další informace najdete v tématu [Postup: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Přidejte vlastní vlastnost. Vlastnost se zobrazí v okně **vlastnosti** při výběru projektu služby SharePoint v **Průzkumník řešení**. Další informace najdete v tématu [Postup: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Návod, který ukazuje, jak vytvořit, nasadit a otestovat rozšíření projektu, naleznete v tématu [Návod: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Pochopení vztahu mezi rozšířeními projektu a instancemi projektu
 Při vytváření rozšíření projektu rozšíření načte, když je otevřen libovolný druh projektu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje několik šablon projektu služby SharePoint, jako jsou například definice seznamů, typy obsahu a přijímače událostí. Existuje však pouze jeden typ projektu služby SharePoint. Typy projektů, které se zobrazí v dialogovém okně **Nový projekt** , jsou pouze šablony, které dohromady seskupí jednu nebo více položek projektu služby SharePoint. Vzhledem k tomu, že existuje pouze jeden typ projektu služby SharePoint, rozšíření vytvořená pro jeden projekt platí pro všechny projekty služby SharePoint. Nemůžete například vytvořit rozšíření, které se vztahuje pouze na projekt **typu obsahu** .

 Chcete-li získat přístup ke konkrétní instanci projektu, zpracujte jednu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> událostí parametru *ProjectService* v implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody. Například chcete-li určit, kdy se projekt služby SharePoint přidá do řešení, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> událost. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Viz také
- [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Postupy: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Návod: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
