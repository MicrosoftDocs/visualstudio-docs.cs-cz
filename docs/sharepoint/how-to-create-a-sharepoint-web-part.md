---
title: 'Postupy: vytvoření webové části služby SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6437620b4215726ba48ea3234e37c76e77d21ebe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120277"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Postupy: vytvoření webové části služby SharePoint
  Můžete vytvořit a upravit webovou část přidáním **webovou část** položky pro všechny projektu služby SharePoint a poté úpravy souboru kódu pro webovou část nebo pomocí návrháře. Další informace najdete v tématu [postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>K vytvoření webové části služby SharePoint
  
1.  Vytvořte nebo otevřete projekt služby SharePoint.  
  
     Další informace najdete v tématu [SharePoint projekt a projekt šablon položek](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Vyberte uzel projektu služby SharePoint v **Průzkumníku řešení** a potom zvolte **projektu** > **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogové okno, rozbalte seznam **SharePoint** uzel a potom zvolte **2010** uzlu.  
  
4.  V seznamu šablon služby SharePoint, zvolte **webovou část**.  
  
5.  V **název** pole, zadejte název pro webové části a pak zvolte **přidat** tlačítko.  
  
     Webové části se zobrazí v **Průzkumníku řešení**. Další informace o souborech, které zahrnuje webovou část najdete v tématu [vytvoření webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  V **Průzkumníku**, otevřete soubor kódu pro webovou část, kterou jste právě vytvořili.  
  
     Například, pokud je název vaší webové části *WebPart1*, otevřete *WebPart1.vb* (v jazyce Visual Basic) nebo *WebPart1.cs* (v jazyku C#).  
  
7.  V souboru kódu přidejte ovládací prvky do metody <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Příklad, naleznete v části [návod: vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Viz také:
 [Vytvoření webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
