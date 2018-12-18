---
title: Rozšíření položek projektu služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b83d5f92a54d58aae2d4c7860e6648920615d63f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823629"
---
# <a name="extend-sharepoint-project-items"></a>Rozšíření položek projektu služby SharePoint
  Vytváření rozšíření položky projektu, pokud chcete přidat funkce do typu položky projektu služby SharePoint, která je již nainstalována v sadě Visual Studio. Například můžete vytvořit rozšíření pro předdefinované **příjemce událostí** nebo **definice seznamu** položky projektu v sadě Visual Studio, nebo můžete vytvořit rozšíření pro vlastní typ položky. Můžete také vytvořit rozšíření pro všechny typy položek Sharepointového projektu.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Úlohy pro rozšíření položky projektu služby SharePoint
 Pro rozšíření položky projektu, vytváření sestavení rozšíření sady Visual Studio, který implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní. Další informace najdete v tématu [postupy: vytváření rozšíření položky projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Když rozšíříte položku projektu, můžete také přidat následující funkce do položky projektu:  
  
- Přidání položky místní nabídky do položky projektu. Položka nabídky se zobrazí, když otevřete místní nabídku pro položku projektu v **Průzkumníka řešení**. Otevřete místní nabídku pravým tlačítkem na položku projektu nebo jej vyberete a potom kliknete **Shift**+**F10** klíče. Další informace najdete v tématu [postupy: Přidání položky místní nabídky do rozšíření položky projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
- Přidání vlastních vlastností do položky projektu. Vlastnost se zobrazí v **vlastnosti** okno při výběru položky projektu v **Průzkumníka řešení**. Další informace najdete v tématu [postupy: Přidání vlastnosti do rozšíření položky projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
  Názorný postup ukazuje, jak vytvořit, nasadit a testování rozšíření položky projektu, naleznete v tématu [návod: rozšíření typu položky projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Pochopení vztahů mezi rozšíření položky projektu a instance položky projektu
 Při vytváření rozšíření položky projektu sady Visual Studio načte vaše rozšíření při přidání položky projektu přidruženého typu do projektu služby SharePoint. Například, pokud vytvoříte rozšíření pro **příjemce událostí** položky projektu sady Visual Studio načte vaše rozšíření když uživatel přidá **příjemce událostí** položku projektu do projektu. Visual Studio používá stejnou instanci rozšíření pro všechny výskyty typ položky přidružený projekt. V předchozím příkladu, pokud uživatel přidá sekundy **příjemce událostí** položku projektu do projektu, stejnou instanci rozšíření se používá k úpravě druhé položky projektu.  
  
 Přístup ke konkrétní instanci rozšiřování typu položky projektu, zpracovat jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> události *projectItemType* parametrů ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody. Například, chcete-li zjistit, kdy je rozšiřování typu položky projektu přidán do projektu, zpracovat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> událostí. Další informace najdete v tématu [postupy: vytváření rozšíření položky projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identifikátory pro položky projektu SharePoint
 Každé položky projektu SharePoint má odpovídající identifikátor řetězce. Identifikátor pro položku projektu musíte vědět, pokud chcete provádět následující úlohy:  
  
- Vytváření rozšíření pro položky projektu. V takovém případě je nutné předat identifikátor pro položku projektu, který chcete rozšířit do konstruktoru <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Chcete-li vytvořit rozšíření pro všechny položky typů projektů, předejte **\\*** hodnotu řetězce.  
  
- Programově přidáte položky projektu do projektu. V takovém případě je nutné předat identifikátor pro položku projektu do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metody.  
  
  Následující tabulka uvádí identifikátory pro položky projektu služby SharePoint, které jsou součástí sady Visual Studio.  
  
|Název položky projektu|Identifikátor řetězce|  
|-----------------------|-----------------------|  
|Model katalogu obchodních dat|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Typ obsahu|Microsoft.VisualStudio.SharePoint.ContentType|  
|Příjemce událostí|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Prázdný Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definice seznamu<br /><br /> Definici seznamu z typu obsahu|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instance seznamu|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modul|Microsoft.VisualStudio.SharePoint.Module|  
|Sekvenční pracovní postup<br /><br /> Pracovní postup stavového stroje|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definice webu|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Vizuální webové části|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Webová část|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulář přidružení pracovního postupu|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytváření rozšíření položky projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Postupy: Přidání položky místní nabídky do rozšíření položky projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Postupy: Přidání vlastnosti do rozšíření položky projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Návod: Rozšíření typu položky projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
