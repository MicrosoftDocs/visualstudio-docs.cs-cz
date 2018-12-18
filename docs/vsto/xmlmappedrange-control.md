---
title: Xmlmappedrange – ovládací prvek
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9cf21ceda64fe79996e05426a3379972c3c4be33
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676132"
---
# <a name="xmlmappedrange-control"></a>Xmlmappedrange – ovládací prvek
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Rozsahu, který se vytvoří pouze v případě, že element neopakujícími schématu je namapována na buňku v aplikaci Microsoft Office Excel je ovládací prvek. Například, když `maxOccurs` atribut na prvek schématu se rovná 1. Poté, co Visual Studio vytvoří rozsah XML, namapované, můžete programovat proti ho přímo bez nutnosti procházení objektovému modelu Excelu. Můžete ho jenom odstranit <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek v rámci aplikace Excel při odebrání mapování elementu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mapování I: použití XML v Excelu?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="bind-data-to-the-control"></a>Vytvoření vazby dat k ovládacímu prvku  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Ovládací prvek podporuje vazbu do jednoho datového pole (jednoduché datové vazby). <xref:Microsoft.Office.Tools.Excel.ListObject> Může ovládací prvek podporuje rozšířené datové vazby a se automaticky vytvoří během opakující se element schématu je namapována na buňku. Další informace najdete v tématu [ListObject – ovládací prvek](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Ovládací prvek vázán na zdroj dat pomocí <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost. Když <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se přidá na buňku listu, Visual Studio automaticky generuje sadu dat z dat v mapovaných buněk a naváže ovládací prvek na této datové sady. Výchozí vazby vlastnosti data <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> je <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Pokud data v vázaný datové sady se aktualizují všechny mechanismem <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek se změny projeví.  
  
## <a name="formatting"></a>Formátování  
 Můžete použít stejný formátování, které se <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek, který lze použít <xref:Microsoft.Office.Interop.Excel.Range>. To zahrnuje ohraničení, písma, formát čísla a styly.  
  
## <a name="events"></a>Události  
 K dispozici pro události <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládacího prvku:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Postupy: Přidání ovládacích prvků XMLMappedRange do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Postupy: mapování schémat na listy v prostředí Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  