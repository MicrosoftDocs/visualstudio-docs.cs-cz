---
title: Rozšíření položek projektu služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967393"
---
# <a name="extend-sharepoint-project-items"></a>Rozšiřování položek projektu služby SharePoint
  Vytvořte rozšíření položky projektu, pokud chcete přidat funkce do typu položky projektu služby SharePoint, která je již nainstalována v aplikaci Visual Studio. Můžete například vytvořit rozšíření pro integrovaný **přijímač událostí** nebo položky projektu **definice seznamu** v aplikaci Visual Studio, nebo můžete vytvořit rozšíření pro vlastní typ položky projektu. Můžete také vytvořit rozšíření pro všechny typy položek projektu služby SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Úlohy pro rozšíření položek projektu služby SharePoint
 Chcete-li rozšířit položku projektu, sestavte sestavení rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Když rozšíříte položku projektu, můžete také do položky projektu přidat následující funkce:

- Přidejte položku místní nabídky do položky projektu. Položka nabídky se zobrazí, když otevřete místní nabídku pro položku projektu v **Průzkumník řešení**. Místní nabídku otevřete tak, že kliknete pravým tlačítkem myši na položku projektu nebo vyberete a pak zvolíte klávesy **SHIFT** + **F10** . Další informace naleznete v tématu [Postupy: Přidání položky místní nabídky do rozšíření položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Přidejte vlastní vlastnost do položky projektu. Vlastnost se zobrazí v okně **vlastnosti** při výběru položky projektu v **Průzkumník řešení**. Další informace naleznete v tématu [Postupy: Přidání vlastnosti do rozšíření položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Návod, který ukazuje, jak vytvořit, nasadit a otestovat rozšíření položky projektu, naleznete v tématu [Návod: rozšíření typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Pochopení vztahu mezi rozšířeními položek projektu a instancemi položek projektu
 Když vytvoříte rozšíření položky projektu, Visual Studio načte rozšíření při přidání položky projektu přidruženého typu do projektu služby SharePoint. Například pokud vytvoříte rozšíření pro položky projektu **přijímače událostí** , Visual Studio načte vaše rozšíření, když uživatel přidá položku projektu **příjemce události** do projektu. Visual Studio používá stejnou instanci rozšíření pro všechny instance přidruženého typu položky projektu. Pokud uživatel v předchozím příkladu přidá do projektu druhou položku projektu **přijímače událostí** , použije se stejná instance rozšíření pro přizpůsobení druhé položky projektu.

 Chcete-li získat přístup ke konkrétní instanci typu položky projektu, kterou rozšiřujete, zpracujte jednu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> událostí parametru *projectItemType* v implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody. Například chcete-li určit, kdy se položka projektu typu, který rozšiřujete, přidá do projektu, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> událost. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identifikátory pro položky projektu služby SharePoint
 Každá položka SharePointového projektu má odpovídající identifikátor řetězce. Je nutné znát identifikátor položky projektu, pokud chcete provádět následující úlohy:

- Vytvořte rozšíření pro položku projektu. V tomto případě musíte předat identifikátor položky projektu, kterou chcete zvětšit na konstruktor <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Chcete-li vytvořit rozšíření pro všechny typy položek projektu, předejte **\\** hodnotu řetězce *.

- Přidejte položku projektu do projektu programově. V takovém případě musíte předat identifikátor položky projektu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metodě.

  V následující tabulce je uveden seznam identifikátorů pro položky projektu služby SharePoint, které jsou součástí sady Visual Studio.

|Název položky projektu|Identifikátor řetězce|
|-----------------------|-----------------------|
|Model obchodní Data Catalog|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Typ obsahu|Microsoft. VisualStudio. SharePoint. ContentType|
|Přijímač událostí|Microsoft. VisualStudio. SharePoint. EventHandler|
|Prázdný element|Microsoft. VisualStudio. SharePoint. GenericElement|
|Definice seznamu<br /><br /> Definice seznamu z typu obsahu|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Instance seznamu|Microsoft. VisualStudio. SharePoint. ListInstance|
|Modul|Microsoft. VisualStudio. SharePoint. Module|
|Sekvenční pracovní postup<br /><br /> Pracovní postup stavového stroje|Microsoft. VisualStudio. SharePoint. Workflow|
|Definice webu|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Vizuální webová část|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Webová část|Microsoft. VisualStudio. SharePoint. WebPart|
|Formulář přidružení pracovního postupu|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Viz také
- [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Postupy: Přidání položky místní nabídky do rozšíření položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Postupy: Přidání vlastnosti do rozšíření položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Návod: rozšiřování typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
