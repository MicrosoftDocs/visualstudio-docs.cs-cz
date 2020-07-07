---
title: 'Postupy: Vytvoření webové části služby SharePoint pomocí návrháře | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016474"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Postupy: Vytvoření webové části služby SharePoint pomocí návrháře
  Můžete vytvořit webovou část přidáním položky **vizuální webové části** do libovolného projektu služby SharePoint. Tím se otevře Návrhář Visual Web Developer v aplikaci Visual Studio, kde můžete přidat ovládací prvky a kód do webové části. Funkce vizuálních webových částí funguje stejným způsobem jako webové části. Jediným rozdílem je, že navrhujete vizuální webové části v návrháři aplikace Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Vytvoření projektu pro Visual Web Parts

1. Na panelu nabídek vyberte **soubor**  > **Nový**  >  **projekt**.

     Otevře se dialogové okno **Nový projekt** .

2. V dialogovém okně **Nový projekt** v části **Visual C#** nebo **Visual Basic**rozbalte uzel **Office/SharePoint** a pak zvolte kategorii **řešení SharePoint** .

3. V seznamu šablon projektu zvolte možnost **SharePoint 2013 – vizuální webová část**a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

4. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL webu SharePointu, který je v místním počítači, a pak klikněte na tlačítko **Dokončit** .

     V **Průzkumník řešení**se zobrazí webová část. Po navržení webové části v návrháři aplikace Visual Web Developer ji otestujete na vámi určeném webu.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Přidání vizuální webové části do existujícího projektu služby SharePoint

1. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte uzel **Office/SharePoint** .

3. V seznamu šablon projektu zvolte možnost **Visual Web Part**, pojmenujte ji a pak klikněte na tlačítko **Přidat** .

     V **Průzkumník řešení**se zobrazí webová část. Po navržení webové části v návrháři aplikace Visual Web Developer ji otestujete na vámi určeném webu.

## <a name="see-also"></a>Viz také:
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
