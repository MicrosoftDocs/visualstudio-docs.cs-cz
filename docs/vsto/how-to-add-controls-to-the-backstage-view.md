---
title: 'Postupy: Přidání ovládacích prvků do zobrazení Backstage '
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b775c7613b8cc0953e419b2546ec017c96e8454
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549074"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Postupy: Přidání ovládacích prvků do zobrazení Backstage
  Návrhář pásu karet můžete použít k přidávání ovládacích prvků do nabídky, které se otevře po kliknutí **souboru** kartě. Při spuštění aplikace, ovládací prvky, které přidáte do **soubor** zobrazí karta skupinu s názvem **doplňky**.  
  
 Před nebo po integrované ovládací prvky nelze umisťování ovládacích prvků pomocí Návrháře pásu karet v sadě Visual Studio. Předdefinované řízení je ovládací prvek, který se již nachází v zobrazení Backstage. Pokud chcete umisťování ovládacích prvků před nebo po integrované ovládací prvky, musíte použít XML pásu karet. Další informace o **pásu karet (XML)**, najdete v části [XML karet](../vsto/ribbon-xml.md). Další informace o přizpůsobení zobrazení Backstage najdete v tématu [Úvod do zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182189) a [přizpůsobit zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Přidání ovládacích prvků do zobrazení Backstage  
  
1.  Otevřete položku pásu karet v zobrazení návrhu.  
  
     Informace o tom, jak přidat **pásu karet (vizuálního návrháře)** položku do projektu, najdete v části [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  V Návrháři pásu karet klikněte **souboru** kartě.  
  
     Zobrazí se návrháře nabídky. Tento návrh prostor neobsahuje všechny ovládací prvky.  
  
3.  Z **ovládacích prvků pásu karet Office** kartě **sada nástrojů**, přetáhněte některý z následujících ovládacích prvků na návrháře nabídky:  
  
    -   Tlačítko  
  
    -   CheckBox  
  
    -   Galerie  
  
    -   Nabídka  
  
    -   Oddělovač  
  
    -   Tlačítko rozdělení  
  
    -   ToggleButton  
  
4.  Přetáhněte ovládací prvky přesunout do nového umístění v nabídce.  
  
## <a name="see-also"></a>Viz také  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Kódu XML pásu karet](../vsto/ribbon-xml.md)   
 [Postupy: Začínáme přizpůsobení pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  