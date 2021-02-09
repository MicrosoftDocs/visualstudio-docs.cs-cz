---
title: 'Postupy: Vytvoření stránky aplikace | Microsoft Docs'
description: Vytvoření webové stránky ASP.NET (označované také jako stránka aplikace) v aplikaci Visual Studio pro jeden nebo více webů SharePointu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74e7aab4cbc012afbf045672dbf4af248ada4c61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925630"
---
# <a name="how-to-create-an-application-page"></a>Postupy: Vytvoření stránky aplikace
  Pro jeden nebo více webů služby SharePoint můžete vytvořit webovou stránku ASP.NET. V SharePointu se tyto stránky nazývají stránky aplikace. Na rozdíl od stránky webu obsahuje stránka aplikace kód, který se spouští za stránkou. Další informace najdete v tématu [Vytvoření stránek aplikace pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Vytvoření stránky aplikace

1. V aplikaci Visual Studio otevřete nebo vytvořte projekt služby SharePoint.

     Další informace naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. V **Průzkumník řešení** vyberte uzel projektu.

3. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

4. V dialogovém okně **Přidat novou položku** rozbalte uzel **SharePoint** a pak zvolte položku **2010** .

5. V seznamu šablon služby SharePoint vyberte možnost **Stránka aplikace**.

6. Do pole **název** zadejte název stránky aplikace a pak klikněte na tlačítko **Přidat** .

     Aplikace Visual Studio přidá do projektu několik složek a souborů. Další informace o těchto souborech najdete v tématu [Vytvoření stránek aplikace pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     V zobrazení **zdroj** v návrháři aplikace Visual Web Developer se zobrazí soubor stránky ASP.NET. Stránku lze navrhnout přidáním ovládacích prvků ze **sady nástrojů** a jejich umístěním do zástupných symbolů obsahu. Další informace naleznete v tématu [zobrazení zdroje, návrhář webových stránek](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Chcete-li zpracovat události řízení, přidejte kód do souboru kódu pro stránku aplikace.

     Soubor kódu se zobrazí, Pokud rozbalíte uzel pro soubor stránky ASP.NET a má příponu *. cs* nebo *. vb* , v závislosti na jazyku projektu. Ucelený příklad vytvoření stránky aplikace naleznete v tématu [Návod: Vytvoření stránky aplikace služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Viz také
- [Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Návod: Vytvoření stránky aplikace služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
