---
title: 'Ukázka rozšíření Excel: Třídy Element | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb5085bdd9a79330f7c4f73fb39993af63eb0a78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811943"
---
# <a name="sample-excel-extension-element-classes"></a>Ukázka rozšíření Excel: Třídy Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření používá třídy, které jsou odvozeny z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> a představují ovládací prvek list a ovládací prvek buňky v [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 Element base pro toto rozšíření je `ExcelElement`. `ExcelWorksheetElement` Třídy a `ExcelCellElement` třída dědí z tohoto elementu  
  
## <a name="element-and-elementinformation-classes"></a>Element a ElementInformation třídy  
 `Element` Je základní třídou pro všechny prvky uživatelského rozhraní pro rozšíření aplikace Excel a dědí z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> třídy. `ElementInformation` je základní třídou pro element třídy informací o v ukázce a nemá žádné členy.  
  
#### <a name="simple-properties-and-methods"></a>Jednoduché vlastnosti a metody  
 Tyto členy vrátí jednoduchých hodnot, jako je například hodnota `Name` vlastnost nebo hodnoty `ClassName` vlastnost a kód je jasný a snadno čitelný. Některé hodnoty jsou vráceny pomocí `Utility` třída, která je popsána dále. Ostatní vrátit `null` protože nejsou v této ukázkové rozšíření relevantní. Dva členové jsou zajímavější, než ostatní: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> vlastnost a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> metoda.  
  
#### <a name="queryid-property"></a>Vlastnost QueryId  
 Tato vlastnost vrátí podmínku, která tvoří páry název hodnota, které jedinečně identifikují ovládacího prvku během přehrávání. Pro každou třídu odvozené ovládací prvek, vývojář musí přepsat tato vlastnost se vraťte <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> objektů, rozhraní framework můžete použít k vyhledání ovládacího prvku v uživatelském rozhraní.  
  
#### <a name="cacheproperties-method"></a>CacheProperties – metoda  
 Tato metoda je volána v rámci testovacího rozhraní během procesu nahrávání říct elementu, který chcete uložit snímek důležité vlastnosti. Tím zůstane vlastnosti, které jsou k dispozici i v případě, že skutečný ovládací prvek uživatelského rozhraní je už na obrazovce.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement a WorksheetInformation třídy  
 `WorksheetElement` Třída představuje Excelového listu v rámci testování a dědí od `Element` základní třídy. Jsou tři vlastnosti potlačena za účelem obsahují podrobné informace o objektu Excelového listu: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>, a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Platí také pro tuto třídu, aby byla viditelná modelu COM.  
  
 `WorksheetInformation` Třída představuje informace o Excelového listu. Má pouze jednoho člena `SheetName` vlastnost, která je pro tuto ukázku dostačující.  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellElement a CellInformation třídy  
 `CellElement` Třída představuje buňku aplikace Excel a dědí od `Element` základní třídy. Je pouze přepsanému členu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> vlastnost, která vrátí <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> , která používá `RowIndex` a `ColumnIndex` vlastnosti k identifikaci buňku.  
  
## <a name="utilities-and-excelutilities-classes"></a>Nástroje a ExcelUtilities třídy  
 Vnitřní `ExcelUtilities` třída poskytuje některé konstantní hodnoty, jako je například název technologie a metodu, která určuje, pokud popisovač okna zadaná představuje Excelový list.  
  
 `Utilities` Třída obsahuje pomocné metody, které vracejí širokou škálu informací o uživatelském rozhraní. Některé metody používají přímá volání do externí systémové knihovny DLL, jako například **USER32. Knihovna DLL** a **OLEACC. Knihovna DLL**, chcete-li získat popisovače okna v uživatelském rozhraní<strong>.</strong>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



