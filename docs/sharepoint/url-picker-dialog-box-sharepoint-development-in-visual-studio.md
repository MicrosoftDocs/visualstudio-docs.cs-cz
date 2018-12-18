---
title: Dialogové okno pro výběr adresy URL (vývoj pro SharePoint v sadě Visual Studio) | Dokumentace společnosti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 517058c99a6ec5a297b95324decbb2cfcbe04271
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950755"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Dialogové okno pro výběr adresy URL (vývoj pro SharePoint v sadě Visual Studio)
  V dialogovém okně pro výběr adresy URL můžete soubory, jako jsou soubory stránky předlohy nebo obrazových souborů, které se nacházejí v projektu nebo na místním serveru, na kterém běží SharePoint.  
  
 Toto dialogové okno se zobrazí, když máte možnost vybrat soubor k nastavení vlastnosti. Toto dialogové okno můžete otevřít kliknutím tlačítko se třemi tečkami (![ASP.NET – Návrhář mobilních řešení Elipsa](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) vedle různé vlastnosti v **vlastnosti** okna. Tlačítko se třemi tečkami se rovněž zobrazuje jako IntelliSense výzvy při přiřazení hodnoty k určité atributy v **zdroj** zobrazení návrháře.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Složky projektu**  
 Zobrazí seznam složek definované v projektu nebo na místním serveru, na kterém běží SharePoint. Klikněte na tlačítko rozšíření zobrazíte podsložky.  
  
 Rozbalte **projektu** uzel k výběru souborů ve vašem projektu. Zobrazit jako volitelných v dialogovém okně, soubory v projektu musí splňovat následující kritéria:  
  
- Soubor musí být součástí mapované složky.  
  
- Soubor musí být přidán do balíčku řešení.  
  
- Soubor nemůže být umístěné v jiném projektu.  
  
  Pokud chcete odkazovat na soubory, které nesplňují tato kritéria, je nutné zadat cestu k souboru ručně.  
  
  Rozbalte **Server** uzel a vyberte soubory, které jsou umístěné na místním serveru, na kterém běží SharePoint. Zobrazit jako volitelných v dialogovém okně, tyto soubory musí splňovat následující kritéria:  
  
- Soubor se musí nacházet v jednom z následujících mapované složky: **image**, **rozložení**, nebo **ControlTemplates**.  
  
- Soubor nemůže být umístěné v databázi obsahu služby SharePoint.  
  
  Pokud chcete odkazovat na soubory, které nesplňují tato kritéria, je nutné zadat cestu k souboru ručně.  
  
  **Obsah složky**  
  Zobrazí seznam souborů ve vybrané složce. Zvolte soubor a klikněte na tlačítko **OK** tlačítka zavřete dialogové okno a odeslat výběr do procesu, která ji zavolala.  
  
  **Soubory typu**  
  Umožňuje vybrat ze seznamu souborů, které jsou vhodné pro úlohu, kterou provádíte.  
  
## <a name="see-also"></a>Viz také:
 [Vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
