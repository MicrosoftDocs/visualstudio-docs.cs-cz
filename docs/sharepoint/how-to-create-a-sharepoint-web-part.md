---
title: 'Postupy: Vytvoření webové části služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a8c02cce2f55374b4d62ba5663e8b3fe85b55b5
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016443"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Postupy: Vytvoření webové části služby SharePoint
  Můžete vytvořit a přizpůsobit webovou část přidáním položky **webové části** do libovolného projektu služby SharePoint a následným úpravou souboru s kódem pro webovou část nebo pomocí návrháře. Další informace naleznete v tématu [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Vytvoření webové části služby SharePoint

1. Vytvořte nebo otevřete projekt služby SharePoint.

     Další informace naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Zvolte uzel projektu služby SharePoint v **Průzkumník řešení** a pak zvolte **projekt**  >  **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V seznamu šablon služby SharePoint vyberte možnost **Webová část**.

5. Do pole **název** zadejte název webové části a pak klikněte na tlačítko **Přidat** .

     Webová část se zobrazí v **Průzkumník řešení**. Další informace o souborech, které webová část obsahuje, najdete v tématu [vytvoření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. V **Průzkumník řešení**otevřete soubor kódu pro webovou část, kterou jste právě vytvořili.

     Například pokud je název vaší webové části *WebPart1*, otevřete *WebPart1. vb* (v Visual Basic) nebo *WebPart1.cs* (v jazyce C#).

7. V souboru kódu přidejte ovládací prvky do metody <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Příklad najdete v tématu [Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Viz také:
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
