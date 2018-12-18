---
title: 'Postupy: Přidání Spouštěče dialogového okna do skupiny pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2513113b473341f2ed099ef0c5ff5961694acb19
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548385"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Postupy: Přidání Spouštěče dialogového okna do skupiny pásu karet
  Spouštěče dialogového okna můžete přidat na žádnou skupinu na pásu karet. Spouštěče dialogového okna je malý ikonu, která se zobrazí ve skupině. Uživatelé kliknou na tuto ikonu otevřete související dialogových oken nebo podokna úloh, které poskytují další možnosti, které se vztahují ke skupině.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Přidání Spouštěče dialogového okna do skupiny pásu karet  
  
1.  Vyberte soubor kódu pásu karet (*VB* nebo *.cs* souboru) v **Průzkumníku řešení**.  
  
2.  Na **zobrazení** nabídky, klikněte na tlačítko **Návrhář**.  
  
3.  Návrhář pásu karet klikněte pravým tlačítkem na všechny skupiny a pak klikněte na **přidat DialogBoxLauncher**.  
  
     Přidejte kód, který <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> událostí skupiny otevřete vlastní nebo integrované dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)   
 [Kódu XML pásu karet](../vsto/ribbon-xml.md)   
 [Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Postupy: Změna polohy karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Postupy: Přidání ovládacích prvků do zobrazení backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Přizpůsobení pásu karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Postupy: zobrazení Add-in chyby uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Návod: Aktualizace ovládacích prvků na pásu karet za běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  