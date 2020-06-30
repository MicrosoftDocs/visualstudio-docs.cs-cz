---
title: 'Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet'
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57918e8a51a3948a2c69eb0c8ab5438b147e44f0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543465"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet
  Položka **pás karet (vizuální Návrhář)** nepodporuje všechny možné typy přizpůsobení pásu karet. Chcete-li pás karet přizpůsobit pokročilým způsobům, můžete vyexportovat pás karet z návrháře na pás XML pásu karet a přímo upravit XML.

> [!NOTE]
> V souboru XML pásu karet nejsou zobrazeny všechny hodnoty vlastností. Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Export pásu karet z Návrháře pásu karet do XML pásu karet

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor kódu pásu karet a pak klikněte na tlačítko **Návrhář zobrazení**.

2. Klikněte pravým tlačítkem myši na Návrhář pásu karet a pak klikněte na **exportovat pás karet do XML**.

     Visual Studio přidá do projektu soubor XML pásu karet a soubor s kódem XML pásu karet.

3. Ve třídě kódu pásu karet vyhledejte komentáře, které začínají na `TODO:` .

4. Zkopírujte blok kódu v těchto komentářích do třídy **ThisAddIn**, **ThisWorkbook**nebo **ThisDocument** v závislosti na typu řešení, které vyvíjíte.

     Tento kód umožňuje aplikaci systém Microsoft Office vyhledat a načíst vlastní pás karet. Další informace najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

5. V třídě **ThisAddIn**, **ThisWorkbook**nebo **ThisDocument** Odkomentujte blok kódu.

     Po zrušení komentáře kódu by měl vypadat podobně jako v následujícím příkladu. V tomto příkladu je volána třída pásu karet `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Přepněte do souboru kódu XML pásu karet a najděte `Ribbon Callbacks` oblast.

     Zde můžete napsat metody zpětného volání pro zpracování akcí uživatele, například kliknutím na tlačítko.

7. Vytvořte metodu zpětného volání pro každou obslužnou rutinu události, kterou jste napsali v kódu Návrháře pásu karet.

8. Přesuňte veškerý kód obslužné rutiny události z obslužných rutin události do metod zpětného volání a upravte kód tak, aby fungoval s programovacím modelem rozšíření pásu karet (Ribbon Extensibility).

     Informace o psaní metod zpětného volání a použití programovacího modelu Ribbon Extensibility naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
