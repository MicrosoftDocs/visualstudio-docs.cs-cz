---
title: 'Postupy: Přidání spouštěče dialogového okna do skupiny pásu karet'
description: Můžete přidat spouštěč dialogového okna do libovolné skupiny na pásu karet, která může otevřít související dialogová okna nebo podokna úloh, která poskytují další možnosti, které se vztahují ke skupině.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d8e04b7549d1b6a458f0993804946502f55f0165
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942279"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Postupy: Přidání spouštěče dialogového okna do skupiny pásu karet
  Spouštěč dialogového okna můžete přidat do libovolné skupiny na pásu karet. Spouštěč dialogového okna je malá ikona, která se zobrazí ve skupině. Uživatelé kliknutím na tuto ikonu otevřou související dialogová okna nebo podokna úloh, která poskytují další možnosti vztahující se ke skupině.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Přidání spouštěče dialogového okna do skupiny pásu karet

1. V **Průzkumník řešení** vyberte soubor kódu pásu karet (soubor *. vb* nebo *. cs* ).

2. V nabídce **zobrazení** klikněte na možnost **Návrhář**.

3. V Návrháři pásu karet klikněte pravým tlačítkem na libovolnou skupinu a pak klikněte na **Přidat DialogBoxLauncher**.

     Přidejte kód do <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> události skupiny a otevřete tak vlastní nebo vestavěné dialogové okno.

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Postupy: Export pásu karet z návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: aktualizace ovládacích prvků na pásu karet v době běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
