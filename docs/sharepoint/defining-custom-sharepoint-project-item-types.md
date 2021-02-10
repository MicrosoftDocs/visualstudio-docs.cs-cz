---
title: Definování vlastních typů položek projektu služby SharePoint | Microsoft Docs
description: Definujte vlastní typ položky projektu služby SharePoint, pokud chcete vytvořit nový typ položky projektu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948866"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definování vlastních typů položek projektu služby SharePoint
  Definujte nový typ položky projektu služby SharePoint, pokud chcete vytvořit nový druh položky projektu služby SharePoint. Například Visual Studio nezahrnuje položky SharePointového projektu pro přidání polí nebo vlastních akcí do webu služby SharePoint. Můžete definovat vlastní typy položek projektu služby SharePoint pro vytváření polí, vlastní akce nebo jiné typy komponent služby SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Úlohy pro definování typů položek projektu služby SharePoint
 Chcete-li definovat vlastní typ položky projektu, sestavte sestavení rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní. Další informace naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Při definování vlastního typu položky projektu můžete také přidat následující funkce do položky projektu:

- Přidejte položku místní nabídky do položky projektu. Položka nabídky se zobrazí po otevření místní nabídky pro položku projektu v **Průzkumník řešení** kliknutím pravým tlačítkem myši na položku projektu nebo výběrem možnosti a následným stisknutím klávesy **SHIFT** + **F10** . Další informace naleznete v tématu [Postupy: Přidání položky místní nabídky do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Přidejte vlastní vlastnost do položky projektu. Vlastnost se zobrazí v okně **vlastnosti** při výběru položky projektu v **Průzkumník řešení**. Další informace naleznete v tématu [Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Chcete-li povolit jiným vývojářům používat položku projektu v aplikaci Visual Studio, vytvořte soubor. spdata a vytvořte šablonu položky nebo šablonu projektu, která je spojena s položkou projektu. Další informace naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Pochopení vztahu mezi typy položek projektu a instancemi položek projektu
 Při definování typu položky projektu služby SharePoint aplikace Visual Studio načte rozšíření při přidání položky projektu přidruženého typu do projektu služby SharePoint. Například pokud definujete nový typ položky projektu **vlastní akce** , Visual Studio načte vaše rozšíření, když uživatel přidá do projektu vlastní položku projektu **Akce** . Visual Studio používá stejnou instanci rozšíření pro všechny instance přidruženého typu položky projektu. Pokud uživatel v předchozím příkladu přidá do projektu druhou položku projektu **vlastní akce** , použije se stejná instance rozšíření pro přizpůsobení druhé položky projektu.

 Chcete-li získat přístup ke konkrétní instanci typu položky projektu, zpracujte jednu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> událostí parametru *ProjectItemTypeDefinition* v implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Například chcete-li zjistit, kdy je položka projektu vlastního typu přidána do projektu, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> událost. Další informace naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Viz také
- [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Postupy: Přidání položky místní nabídky do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
