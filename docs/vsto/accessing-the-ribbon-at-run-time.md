---
title: Přístup k pásu karet za běhu
description: Můžete napsat kód pro zobrazení, skrytí a úpravu pásu karet a povolit uživatelům spouštění kódu z ovládacích prvků ve vlastním podokně úloh, podokně akce nebo oblasti formuláře aplikace Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 224396d7b4328164c55bc58c746909ada015e02f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965730"
---
# <a name="access-the-ribbon-at-run-time"></a>Přístup k pásu karet za běhu
  Můžete napsat kód pro zobrazení, skrytí a úpravu pásu karet a povolit uživatelům spouštění kódu z ovládacích prvků ve vlastním podokně úloh, podokně akce nebo oblasti formuláře aplikace Outlook.

 K pásu karet můžete přistupovat pomocí `Globals` třídy. Pro projekty Outlook máte přístup k pás karet, které se zobrazí v konkrétním okně nástroje Outlook Inspector nebo Outlook Exploreru.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Přístup k pásu karet pomocí třídy Globals
 Třídu můžete použít `Globals` pro přístup k pásu karet v projektu na úrovni dokumentu nebo v projektu doplňku VSTO z libovolného místa v projektu.

 Další informace o `Globals` třídě naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

 Následující příklad používá `Globals` třídu pro přístup k vlastnímu pásu karet s názvem `Ribbon1` a nastavení textu, který se zobrazí na poli se seznamem na pásu karet na `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Přístup ke kolekci pásu karet, která se zobrazí v konkrétním okně kontroly aplikace Outlook
 Můžete získat přístup ke kolekci pásu karet, která se zobrazí v *okně kontroly* aplikace Outlook. Inspektor je okno, které se otevře v aplikaci Outlook, když uživatelé provádějí určité úkoly, například vytváření e-mailových zpráv. Chcete-li získat přístup k pásu karet okna inspektora, zavolejte `Ribbons` vlastnost `Globals` třídy a předejte <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který představuje inspektor.

 Následující příklad získá kolekci pásu karet inspektoru, který aktuálně má fokus. Tento příklad pak přistupuje k pojmenovanému pásu karet `Ribbon1` a nastaví text, který se zobrazí na poli se seznamem na pásu karet na `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Přístup ke kolekci pásu karet, která se zobrazí pro konkrétní aplikaci Outlook Explorer
 Můžete získat přístup ke kolekci pásu karet, která se zobrazí v aplikaci Outlook *Explorer*. Průzkumník je hlavním uživatelským rozhraním aplikace (UI) pro instanci Outlooku. Chcete-li získat přístup k pásu karet okna Průzkumníka, zavolejte `Ribbons` vlastnost `Globals` třídy a předejte <xref:Microsoft.Office.Interop.Outlook.Explorer> objekt, který představuje Průzkumníka.

 Následující příklad načte kolekci pásu karet Průzkumníka, který aktuálně má fokus. Tento příklad pak přistupuje k pojmenovanému pásu karet `Ribbon1` a nastaví text, který se zobrazí na poli se seznamem na pásu karet na `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: aktualizace ovládacích prvků na pásu karet v době běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
