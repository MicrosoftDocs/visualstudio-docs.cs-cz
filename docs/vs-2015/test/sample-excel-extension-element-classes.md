---
title: 'Ukázka rozšíření aplikace Excel: třídy elementů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21c7777be710f0175708629eb9507b34f0d70be2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660455"
---
# <a name="sample-excel-extension-element-classes"></a>Ukázka rozšíření Excel: Třídy Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření používá třídy, které jsou odvozeny z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> a představují ovládací prvek listu a ovládací prvek buňky v [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

 Základní prvek pro toto rozšíření je `ExcelElement` . `ExcelWorksheetElement`Třída a `ExcelCellElement` Třída dědí z daného elementu.

## <a name="element-and-elementinformation-classes"></a>Třídy elementů a ElementInformation
 `Element`Je základní třídou pro všechny prvky uživatelského rozhraní pro rozšíření aplikace Excel a dědí z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> třídy. `ElementInformation` je základní třídou tříd informací o elementu v ukázce a nemá žádné členy.

#### <a name="simple-properties-and-methods"></a>Jednoduché vlastnosti a metody
 Tyto členy vracejí jednoduché hodnoty, jako je hodnota `Name` vlastnosti nebo hodnota `ClassName` vlastnosti, a kód je jasný a snadno čitelný. Některé hodnoty jsou vráceny pomocí `Utility` třídy, která je popsána později. Ostatní se vrátí, `null` protože nejsou relevantní v tomto ukázkovém rozšíření. Dva členové jsou zajímavější než ostatní: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> vlastnost a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> metoda.

#### <a name="queryid-property"></a>Vlastnost QueryId
 Tato vlastnost vrací podmínku, která je tvořena páry název-hodnota, které jedinečně identifikují ovládací prvek během přehrávání. Pro každou odvozenou třídu ovládacího prvku musí vývojář tuto vlastnost přepsat, aby vrátila <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> objekt, který může rozhraní použít k vyhledání ovládacího prvku v uživatelském rozhraní.

#### <a name="cacheproperties-method"></a>Metoda CacheProperties
 Tato metoda je volána rozhraním testování během procesu zaznamenávání, aby informovala, že element ukládá snímek důležitých vlastností. Tím zůstanou dostupné vlastnosti i v případě, že vlastní ovládací prvek uživatelského rozhraní už není na obrazovce.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>Třídy WorksheetElement a WorksheetInformation
 `WorksheetElement`Třída představuje excelový list v testovacím rozhraní a dědí ze `Element` základní třídy. Tři vlastnosti jsou přepsány tak, aby poskytovaly konkrétní informace o objektu sešitu aplikace Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A> , <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> , a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A> .

 Pro <xref:System.Runtime.InteropServices.ComVisibleAttribute> tuto třídu se používá také, aby byla viditelná pro model COM.

 `WorksheetInformation`Třída představuje informace o excelovém listu. Má pouze jednoho člena, `SheetName` vlastnost, která je pro tuto ukázku dostačující.

## <a name="cellelement-and-cellinformation-classes"></a>Třídy CellElement a CellInformation
 `CellElement`Třída reprezentuje buňku aplikace Excel a dědí ze `Element` základní třídy. Jediným přepsaným členem je <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> vlastnost, která vrátí hodnotu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> , která `RowIndex` `ColumnIndex` pro identifikaci buňky používá vlastnosti a.

## <a name="utilities-and-excelutilities-classes"></a>Třídy nástrojů a ExcelUtilities
 Interní `ExcelUtilities` Třída poskytuje některé konstantní hodnoty, jako je název technologie, a metodu, která určuje, zda poskytnutý popisovač okna představuje excelový list.

 `Utilities`Třída obsahuje pomocné metody, které vracejí různé informace o uživatelském rozhraní. Některé metody používají přímé volání do externích systémových knihoven DLL, jako je například **USER32.DLL** a **OLEACC.DLL**, k získání POPISOVAČŮ okna z uživatelského rozhraní<strong>.</strong>

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
