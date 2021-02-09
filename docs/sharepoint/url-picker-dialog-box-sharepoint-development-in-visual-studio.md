---
title: Dialogové okno pro výběr adresy URL (vývoj pro SharePoint)
description: Přečtěte si o dialogovém okně pro výběr adresy URL, které umožňuje uživateli zvolit soubory ve svém projektu nebo na místním serveru, na kterém je spuštěna služba SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d04857f0e61e5d9f293d73902cd090f718c65cd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892213"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Dialogové okno pro výběr adresy URL (vývoj pro SharePoint v aplikaci Visual Studio)
  V dialogovém okně pro výběr adresy URL můžete zvolit soubory, jako jsou soubory stránky předlohy nebo soubory obrázků, které jsou umístěné ve vašem projektu, nebo na místním serveru, na kterém je spuštěna služba SharePoint.

 Toto dialogové okno se zobrazí, když máte možnost zvolit soubor pro nastavení vlastnosti. Toto dialogové okno můžete otevřít kliknutím na tlačítko se třemi tečkami (![elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) vedle různých vlastností v okně **vlastnosti** . Tlačítko se třemi tečkami se také zobrazí jako výzva IntelliSense při přiřazování hodnot k určitým atributům v zobrazení **zdroje** v návrháři.

## <a name="uielement-list"></a>UIElement – seznam
 **Složky projektu** Zobrazí seznam složek definovaných v projektu nebo na místním serveru, na kterém je spuštěna služba SharePoint. Kliknutím na tlačítko rozšíření zobrazíte podsložky.

 Rozbalením uzlu **projektu** vyberte soubory v projektu. Aby se v dialogovém okně zobrazovala možnost vybratelné, soubory v projektu musí splňovat následující kritéria:

- Soubor musí být obsažen v mapované složce.

- Soubor musí být přidán do balíčku řešení.

- Soubor se nemůže nacházet v jiném projektu.

  Pokud chcete odkazovat na soubory, které nesplňují tato kritéria, je nutné zadat cestu k souboru ručně.

  Rozbalte uzel **Server** a vyberte soubory nacházející se na místním serveru, na kterém je spuštěna služba SharePoint. Aby se v dialogovém okně zobrazovala možnost výběru, musí tyto soubory splňovat následující kritéria:

- Soubor se musí nacházet v jedné z následujících mapovaných složek: **Image**, **rozložení** nebo **ControlTemplates**.

- Soubor se nenašel v databázi obsahu SharePointu.

  Pokud chcete odkazovat na soubory, které nesplňují tato kritéria, je nutné zadat cestu k souboru ručně.

  **Obsah složky** Zobrazí seznam souborů ve vybrané složce. Zvolte soubor a potom kliknutím na tlačítko **OK** zavřete dialogové okno a odešlete svůj výběr do procesu, který ho volal.

  **Soubory typu** Umožňuje vybrat ze seznamu souborů, které jsou vhodné pro úlohu, kterou provádíte.

## <a name="see-also"></a>Viz také
- [Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
