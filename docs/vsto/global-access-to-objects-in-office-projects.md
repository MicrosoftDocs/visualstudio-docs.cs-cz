---
title: Globální přístup k objektům v projektech pro systém Office
description: Přečtěte si, jak lze použít třídu Globals pro přístup k několika různým projektovým položkám v době běhu z libovolného kódu v projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5786ea4bdd0dd6f4c92284aaf9cff2a3c95e4231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920491"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globální přístup k objektům v projektech pro systém Office
  Při vytváření projektu sady Office sada Visual Studio automaticky generuje třídu s názvem `Globals` v projektu. Třídu můžete použít `Globals` pro přístup k několika různým projektovým položkám v době běhu z libovolného kódu v projektu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Jak použít třídu Globals
 `Globals` je statická třída, která udržuje odkazy na určité položky v projektu. Pomocí `Globals` třídy můžete získat přístup k následujícím položkám z libovolného kódu v projektu v době běhu:

- `ThisWorkbook`Třídy a `Sheet` *n* v excelovém sešitu nebo šabloně projektu. K těmto objektům můžete přistupovat pomocí `Globals.ThisWorkbook` vlastností a `Sheet` *n* .

- `ThisDocument`Třída ve wordovém dokumentu nebo šabloně projektu. K tomuto objektu můžete přistupovat pomocí `Globals.ThisDocument` Vlastnosti.

- `ThisAddIn`Třída v projektu doplňku VSTO. K tomuto objektu můžete přistupovat pomocí `Globals.ThisAddIn` Vlastnosti.

- Všechny pásy v projektu, které jste přizpůsobili pomocí Návrháře pásu karet. K pás karet můžete přistupovat pomocí `Globals.Ribbons` Vlastnosti. Další informace najdete v tématu [přístup k pásu karet v době běhu](../vsto/accessing-the-ribbon-at-run-time.md).

- Všechny oblasti formulářů aplikace Outlook v projektu doplňku aplikace Outlook VSTO. K oblastem formuláře můžete přistupovat pomocí `Globals.FormRegions` Vlastnosti. Další informace najdete v tématu [přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md).

- Objekt factory, který umožňuje vytvořit ovládací prvky pásu karet a položky hostitele v době běhu v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . K tomuto objektu můžete přistupovat pomocí `Globals.Factory` Vlastnosti. Tento objekt je instancí třídy, která implementuje jedno z následujících rozhraní:

  - [Microsoft. Office. Tools. Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft. Office. Tools. Excel. Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft. Office. Tools. Outlook. Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft. Office. Tools. Word. Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Můžete například použít `Globals.Sheet1` vlastnost pro vložení textu do <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku, `Sheet1` když uživatel klikne na tlačítko v podokně akce v projektu na úrovni dokumentu v aplikaci Excel.

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

 Kód, který se pokusí použít `Globals` třídu před inicializací dokumentu nebo doplňku VSTO, může vyvolat výjimku za běhu. Například použití `Globals` při deklaraci proměnné na úrovni třídy může selhat, protože `Globals` třída nemusí být inicializována s odkazy na všechny položky hostitele před vytvořením instance deklarovaného objektu.

> [!NOTE]
> `Globals`Třída není nikdy inicializována v době návrhu, ale instance ovládacích prvků jsou vytvořeny návrhářem. To znamená, že pokud vytvoříte uživatelský ovládací prvek, který používá vlastnost `Globals` třídy v rámci třídy uživatelského ovládacího prvku, je nutné před pokusem o použití vráceného objektu ověřit, zda vlastnost vrací **hodnotu null** .

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Položka hostitele dokumentu](../vsto/document-host-item.md)
- [Položka hostitele sešitu](../vsto/workbook-host-item.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
