---
title: 'Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f1b9e988ce6d1ad722766f3994c39827cc4272a3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255074"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet
  **Pásu karet (vizuálního návrháře)** položku nepodporuje všechny možné typy přizpůsobení pásu karet. Přizpůsobení pásu karet pokročilé způsoby, můžete exportovat na pásu karet z Návrháře do kódu XML pásu karet a přímo upravit soubor XML.  
  
> [!NOTE]  
>  Ne všechny hodnoty vlastností se zobrazí v souboru XML pásu karet. Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Export pásu karet z Návrháře pásu karet do kódu XML pásu karet  
  
1.  Klikněte pravým tlačítkem na pásu karet souboru kódu v **Průzkumníku řešení**a potom klikněte na **Návrhář zobrazení**.  
  
2.  Klikněte pravým tlačítkem na Návrháře pásu karet a pak klikněte na **Export pásu karet na XML**.  
  
     Visual Studio přidá soubor XML pásu karet a soubor kódu XML pásu karet do projektu.  
  
3.  Ve třídě kódu pásu karet najděte komentáře, které začínají `TODO:`.  
  
4.  Zkopírujte blok kódu v těchto komentáře **ThisAddin**, **ThisWorkbook**, nebo **ThisDocument** třídy, v závislosti na tom, jaký typ řešení vyvíjíte.  
  
     Tento kód umožňuje aplikaci Microsoft Office ke zjištění a načíst vaše vlastní pás karet. Další informace najdete v tématu [XML karet](../vsto/ribbon-xml.md).  
  
5.  V **ThisAddin**, **ThisWorkbook**, nebo **ThisDocument** třídy, zrušte komentář kódu bloku.  
  
     Po zrušte komentář u kód by měl podobat následujícímu příkladu. V tomto příkladu je volána třída pásu karet `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Přepněte do souboru kódu XML pásu karet a najít `Ribbon Callbacks` oblast.  
  
     Toto je, kde můžete psát metody zpětného volání pro zpracování akce uživatele, například kliknutí na tlačítko.  
  
7.  Vytvoření metody zpětného volání pro každou obslužnou rutinu události, který jste napsali v kódu Návrhář pásu karet.  
  
8.  Přesunout všechny kód obslužné rutiny události z obslužné rutiny událostí do metody zpětného volání a upravte kód pro práci s programovací model rozšiřitelnosti pásu karet (RibbonX).  
  
     Informace o psaní metody zpětného volání a pomocí programovacího modelu RibbonX najdete v tématu [XML karet](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Kódu XML pásu karet](../vsto/ribbon-xml.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  