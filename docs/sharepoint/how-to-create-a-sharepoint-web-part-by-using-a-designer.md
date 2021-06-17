---
title: 'Postupy: Vytvoření webové části služby SharePoint pomocí návrháře | Microsoft Docs'
titleSuffix: ''
description: Vytvořte webovou část přidáním položky webové části vizuálu do projektu SharePointu, který otevře návrháře webových vývojářů ve visual web developeru Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112391"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Postupy: Vytvoření webové části služby SharePoint pomocí návrháře

  Webovou část můžete vytvořit přidáním položky webové **části** vizuálu do libovolného sharepointového projektu. Tím se otevře návrhář visual web developer v Visual Studio, kde můžete do webové části přidat ovládací prvky a kód. Webové části vizuálu fungují stejně jako webové části. Jediným rozdílem je, že vizuální webové části můžete navrhovat v návrháři Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Vytvoření projektu pro vizuální webové části

1. Na řádku nabídek zvolte File New Project **(Soubor**  > **nový**  >  **projekt).**
::: moniker range="=vs-2017"

2. V dialogovém **okně Nový** projekt v části **Visual C#** **nebo Visual Basic** rozbalte uzel **Office/SharePoint** a pak zvolte kategorii **Řešení služby SharePoint.**

3. V seznamu šablon projektů zvolte **SharePoint 2013 – Webová** část vizuálu a pak zvolte **tlačítko OK.**

     Zobrazí **se Průvodce přizpůsobením SharePointu.**
::: moniker-end
::: moniker range=">=vs-2019"
2. V dialogovém **okně Vytvořit nový projekt** vyberte *sharepointovou* vizuální webovou část * pro konkrétní verzi SharePointu, kterou jste nainstalovali. Pokud máte například instalaci SharePointu 2019, vyberte šablonu webové části **SharePoint 2019 – Visual.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Pokud chcete, změňte název projektu a pak zvolte **tlačítko** Vytvořit.

::: moniker-end
4. Na **stránce Zadejte web** a úroveň zabezpečení pro ladění zadejte adresu URL sharepointového webu, který je na místním počítači, a pak zvolte **tlačítko** Dokončit.

     V **Průzkumník řešení** se zobrazí webová část. Po navržení webové části v návrháři Visual Web Developer ji otestujte na webu, který zadáte.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Přidání webové části vizuálu do existujícího projektu SharePointu

1. V řádku nabídek zvolte Project Add New Item **(Projekt**  >  **– přidat novou položku).**

2. V **dialogovém okně Přidat** novou položku zvolte uzel **Office/SharePoint.**

3. V seznamu šablon projektů zvolte Visual Web Part (Webová **část vizuálu),** pojmete ji a pak zvolte tlačítko Add **(Přidat).**

     V **Průzkumník řešení** se zobrazí vaše webová část. Po navržení webové části v návrháři Visual Web Developer ji otestujte na webu, který zadáte.

## <a name="see-also"></a>Viz také

- [Vytváření webových částí pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Návod: Vytvoření webové části pro SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Návod: Vytvoření webové části pro SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
