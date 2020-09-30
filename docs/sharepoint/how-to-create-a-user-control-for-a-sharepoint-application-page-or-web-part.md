---
title: Vytvořit uživatelský ovládací prvek pro stránku aplikace SharePoint nebo webovou část
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9c8a99562d937d7b10c3539888c2dd62eb1d1da
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584097"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Postupy: vytvoření uživatelského ovládacího prvku pro stránku aplikace SharePoint nebo webovou část
  Můžete také vytvářet vlastní uživatelské ovládací prvky, které poskytují vlastní funkce pro řešení služby SharePoint, a tyto funkce v rámci svého projektu znovu využívat. De webové části nebo do stránky aplikace lze zahrnout uživatelské ovládací prvky, přidat další ovládací prvky technologie ASP.NET, ovládací prvky služby SharePoint a definovat vlastnosti a metody pro ovládací prvek. Další informace o uživatelských ovládacích prvcích naleznete v tématu [Create recyklovatelné ovládací prvky pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) a [uživatelské ovládací prvky a ovládací prvky serveru v SharePointu](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Vytvoření uživatelského ovládacího prvku služby SharePoint.

1. V aplikaci Visual Studio otevřete nebo vytvořte projekt služby SharePoint.

     Viz [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. V **Průzkumník řešení**vyberte uzel projektu.

3. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

     Otevře se dialogové okno **Přidat novou položku** .

4. V podokně **nainstalováno** vyberte uzel **Office/SharePoint** .

5. V seznamu šablon služby SharePoint vyberte možnost **uživatelský ovládací prvek (pouze řešení farmy)**.

    > [!NOTE]
    > Uživatelské ovládací prvky fungují pouze pro řešení farmy.

6. Do pole **název** zadejte název uživatelského ovládacího prvku a pak klikněte na tlačítko **Přidat** .

     Aplikace Visual Studio přidá do projektu několik složek a souborů. Další informace o těchto souborech najdete v tématu [vytvoření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Ve výchozím nastavení se soubor uživatelského ovládacího prvku zobrazí v zobrazení **zdroj** v návrháři aplikace Visual Web Developer. V tomto zobrazení lze upravit značku XML ovládacího prvku. Pokud chcete ovládací prvek vizuálně navrhovat přetažením ovládacích prvků ze **sady nástrojů**, můžete přepnout do **návrhového** zobrazení. Viz [návrhové zobrazení, návrhář webových stránek](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Pokud chcete zpracovávat události, ke kterým došlo v ovládacím prvku, přidejte kód do souboru kódu uživatelského ovládacího prvku.

     Tento soubor se zobrazí v **Průzkumník řešení** v souboru uživatelského ovládacího prvku a má příponu *. cs* nebo *. vb* v závislosti na jazyku projektu.

## <a name="see-also"></a>Viz také
- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
