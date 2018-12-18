---
title: Globální přístup k objektům v projektech pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 018ffc5c165c8cea7df66911c71f636712df4229
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932036"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globální přístup k objektům v projektech pro systém Office
  Při vytváření projektu aplikace Office, Visual Studio automaticky vygeneruje třídu pojmenovanou `Globals` v projektu. Můžete použít `Globals` pro přístup k několika položek jiného projektu za běhu v žádném kódu v projektu.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Jak používat Globals – třída  
 `Globals` je statická třída, která zajišťuje odkazy na některé položky ve vašem projektu. S použitím `Globals` třídy, následující položky se dá dostat z žádný kód v projektu za běhu:  
  
- `ThisWorkbook` a `Sheet` *n* třídy v projektu sešitu nebo šabloně aplikace Excel. Můžete přístup k těmto objektům s použitím `Globals.ThisWorkbook` a `Sheet` *n* vlastnosti.  
  
- `ThisDocument` Třídy v projektu dokumentu nebo šabloně aplikace Word. Můžete přístup k tomuto objektu pomocí `Globals.ThisDocument` vlastnost.  
  
- `ThisAddIn` Třídu v projektu doplňku VSTO. Můžete přístup k tomuto objektu pomocí `Globals.ThisAddIn` vlastnost.  
  
- Všechny pásy karet v projektu, který můžete přizpůsobit pomocí Návrháře pásu karet. Pásy přístupné prostřednictvím `Globals.Ribbons` vlastnost. Další informace najdete v tématu [přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md).  
  
- Všechny oblastí formulářů aplikace Outlook v projektu doplňku VSTO v Outlooku. Můžete přístup k oblasti formuláře pomocí `Globals.FormRegions` vlastnost. Další informace najdete v tématu [přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md).  
  
- Objekt factory, který vám umožní vytvořit ovládací prvky pásu karet a hostovat položky v době běhu v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Můžete přístup k tomuto objektu pomocí `Globals.Factory` vlastnost. Tento objekt je instancí třídy, která implementuje jednu následujících rozhraní:  
  
  -   <xref:Microsoft.Office.Tools.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
  Například můžete použít `Globals.Sheet1` vlastnost vložit text do <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládání na `Sheet1` když uživatel klikne na tlačítko v podokně akcí v projektu úrovni dokumentu pro Excel.  
  
  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initialize-the-globals-class"></a>Inicializovat Globals – třída  
 Kód, který se pokouší použít `Globals` třídy před inicializací dokumentu nebo doplňku VSTO může vyvolat výjimku běhu. Například použití `Globals` při deklarování proměnné úrovni třídy může selhat, protože `Globals` třída nebyla pravděpodobně inicializována s odkazy na všechny položky hostitele před vytvořením instance deklarovanému objektu.  
  
> [!NOTE]  
>  `Globals` Třída je inicializována nikdy v době návrhu, ale v návrháři se vytvářejí instance ovládacího prvku. To znamená, že je-li vytvořit uživatelský ovládací prvek, který používá vlastnost `Globals` třídy z uvnitř třídy uživatelského ovládacího prvku, je nutné, zda vlastnost vrací **null** předtím, než se pokusíte použít vráceného objektu.  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Hostitelská položka Document](../vsto/document-host-item.md)   
 [Hostitelská položka Workbook](../vsto/workbook-host-item.md)   
 [Hostitelská položka Worksheet](../vsto/worksheet-host-item.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  