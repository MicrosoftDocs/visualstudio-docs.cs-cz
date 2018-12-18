---
title: Rozšíření projektů SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56e714f910a2421a909cba6714e65d21b66991ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835836"
---
# <a name="extend-sharepoint-projects"></a>Rozšíření projektů SharePoint
  Vytváření rozšíření projektu, pokud chcete přizpůsobit funkce na úrovni projektu projektů služby SharePoint. Můžete například přidat vlastní vlastnosti projektu nebo reakce na události na úrovni projektu, které jsou vyvolány, když uživatel vyvíjí řešení služby SharePoint v sadě Visual Studio.  
  
## <a name="create-project-extensions"></a>Vytváření rozšíření projektu
 Pro rozšíření položky projektu, vytváření sestavení rozšíření sady Visual Studio, který implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Další informace najdete v tématu [postupy: vytváření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Při vytváření rozšíření projektu můžete také přidat následující funkce do projektů služby SharePoint:  
  
- Přidání položky místní nabídky. Položka nabídky se zobrazí, když otevřete místní nabídku pro uzel projektu služby SharePoint v **Průzkumníka řešení** tak, že pravým tlačítkem myši uzel nebo jej vyberete a potom kliknete **Shift** +  **F10** klíče. Další informace najdete v tématu [postupy: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
- Přidáte vlastní vlastnost. Vlastnost se zobrazí v **vlastnosti** okno při výběru projektu služby SharePoint v **Průzkumníka řešení**. Další informace najdete v tématu [postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
  Názorný postup ukazuje, jak vytvořit, nasadit a testovat rozšíření projektu, naleznete v tématu [návod: vytváření rozšíření projektu služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Porozumět vztahu mezi instance projektu a projekt rozšíření
 Při vytváření rozšíření projektu rozšíření načte při otevření jakékoliv projektu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje několik šablon projektu služby SharePoint, jako je například seznam definic, typy obsahu a příjemci událostí. Je však pouze jeden typ projektu služby SharePoint. Typy projektů, které se zobrazují v **nový projekt** dialogové okno se pouze šablony, které pohromadě jeden nebo více položek projektu služby SharePoint. Protože se nachází pouze jeden typ projektu služby SharePoint, rozšíření pro jeden projekt vytvoří platí pro všechny projekty služby SharePoint. Nelze například vytvořit rozšíření, které platí pro pouze **typ obsahu** projektu.  
  
 Pro přístup k instanci určitého projektu, zpracovat jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> události *projectService* parametrů ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody. Například chcete-li zjistit, kdy projektu služby SharePoint je přidán do řešení, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> událostí. Další informace najdete v tématu [postupy: vytváření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytváření rozšíření projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Postupy: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Návod: Vytváření rozšíření projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Rozšíření položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Rozšíření balení a nasazení SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
