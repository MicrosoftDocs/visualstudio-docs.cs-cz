---
title: 'Postupy: Add-in zobrazení chyb uživatelského rozhraní'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd6da0c83d0dee835169a0a8068af8d75facbbd4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676023"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Postupy: Add-in zobrazení chyb uživatelského rozhraní
  Ve výchozím nastavení pokud doplňku VSTO pokusí pracovat s Microsoft Office uživatelského rozhraní (UI) a selže, žádná se chybová zpráva. Můžete ale nakonfigurovat aplikace Microsoft Office pro zobrazení zprávy pro chyby, které se vztahují na uživatelské rozhraní. Tyto zprávy můžete použít k určení toho, proč se nezobrazí vlastní pás karet nebo proč se zobrazí pásu karet, ale žádné ovládací prvky se zobrazí.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>K zobrazení chyb rozhraní uživatele doplňku VSTO  
  
1.  Spusťte aplikaci.  
  
2.  Klikněte na tlačítko **souboru** kartu.  
  
3.  Klikněte na tlačítko **možnosti**.  
  
4.  V podokně kategorie, klikněte na tlačítko **Upřesnit**.  
  
5.  V podokně podrobností vyberte **doplňku VSTO zobrazení chyb uživatelského rozhraní**a potom klikněte na tlačítko **OK**.  
  
    > [!NOTE]  
    >  Pro aplikaci Outlook **doplňku VSTO zobrazení chyb uživatelského rozhraní** zaškrtávacího políčka se nachází v **Developer** části podokna podrobností. U ostatních aplikací se nachází na zaškrtávací políčko v **Obecné** části podokna podrobností.  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)  
  
  