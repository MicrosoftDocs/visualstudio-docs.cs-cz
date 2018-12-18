---
title: Přístup k pásu karet za běhu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a20297ee0d60173cbd0513f3d34e12f12388bdb
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304620"
---
# <a name="access-the-ribbon-at-runtime"></a>Přístup k pásu karet za běhu
  Můžete napsat kód k zobrazení, skrytí a změnám pásu karet a povolit uživatelům spouštět kód z ovládacích prvků v vlastního podokna úloh, podokna akcí nebo oblasti formuláře aplikace Outlook.  

 Na pásu karet přístupné prostřednictvím `Globals` třídy. Pro projekty aplikace Outlook dostanete pásů karet, které se zobrazují v konkrétní okno Kontrola aplikace Outlook nebo Outlook Explorer.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Přístup k pásu karet pomocí Globals – třída  
 Můžete použít `Globals` pro přístup k pásu karet v projektech na úrovni dokumentu nebo v projektu doplňku VSTO z libovolného místa v projektu.  

 Další informace o `Globals` najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  

 V následujícím příkladu `Globals` pro přístup k vlastní pás karet s názvem `Ribbon1` a nastavit text, který se zobrazí na pole se seznamem na pásu karet `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Přístup ke kolekci pásů karet, které se zobrazí v okně konkrétní aplikace Outlook inspektoru  
 Kolekce pásů karet, které se zobrazují v Outlooku dostanete *kontroly*. Kontrolor je okno, které se otevře v Outlooku, když uživatelé provedou určité úlohy, jako je například vytváření e-mailové zprávy. Chcete-li získat přístup k pásu karet inspektoru okna, zavolejte `Ribbons` vlastnost `Globals` třídy a předejte mu <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který reprezentuje inspektor.  

 Následující příklad získá kolekci pásu karet inspektoru, který má aktuálně fokus. Tento příklad následně přistupuje k pás karet s názvem `Ribbon1` a nastaví text, který se zobrazí na pole se seznamem na pásu karet `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Přístup ke kolekci pásů karet, které se zobrazují pro konkrétní aplikaci Outlook Explorer  
 Dostanete kolekce pásů karet, které se zobrazují v aplikace Outlook *Explorer*. Průzkumníka je hlavní aplikace uživatelské rozhraní (UI) pro instanci aplikace Outlook. Chcete-li získat přístup k pásu karet okno Průzkumníka, zavolejte `Ribbons` vlastnost `Globals` třídy a předejte mu <xref:Microsoft.Office.Interop.Outlook.Explorer> objekt, který reprezentuje v Průzkumníku.  

 Následující příklad získá kolekci pásu karet Explorer, který má aktuálně fokus. Tento příklad následně přistupuje k pás karet s názvem `Ribbon1` a nastaví text, který se zobrazí na pole se seznamem na pásu karet `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Pás karet – XML](../vsto/ribbon-xml.md)   
 [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Návod: Aktualizace ovládacích prvků na pásu karet za běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)  
