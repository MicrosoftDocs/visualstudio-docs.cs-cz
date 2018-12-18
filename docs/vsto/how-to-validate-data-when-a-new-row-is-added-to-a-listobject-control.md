---
title: 'Postupy: ověření dat při přidání nového řádku do ovládacího prvku ListObject'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268357"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Postupy: ověření dat při přidání nového řádku do ovládacího prvku ListObject
  Uživatele můžete přidat nové řádky, které <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který je vázaný na data. Před potvrzením změny ke zdroji dat můžete ověřit data uživatele.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Ověřování dat  
 Vždy, když se přidá řádek do <xref:Microsoft.Office.Tools.Excel.ListObject> k datům, která je vázaná <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> událost se vyvolá. Dokáže zpracovat tuto událost, chcete-li provést ověření vaše data. Například pokud vaše aplikace vyžaduje, že lze přidat pouze zaměstnanci věku 18 do 65 ke zdroji dat, ověřte, že stáří zadali spadá do rozsahu předtím, než se přidá řádek.  
  
> [!NOTE]  
>  Vždy byste měli zkontrolovat vstup uživatele na serveru kromě klienta. Další informace najdete v tématu [zabezpečit klientské aplikace](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Pro ověření dat při nový řádek je přidat do vázané na data ListObject  
  
1.  Vytváření proměnných pro ID a <xref:System.Data.DataTable> na úrovni třídy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Vytvořte novou <xref:System.Data.DataTable> a přidejte ukázkový sloupce a data v `Startup` obslužnou rutinu události `Sheet1` – třída (v projektech na úrovni dokumentu) nebo `ThisAddIn` – třída (v projektu doplňku VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Přidejte kód, který `list1_BeforeAddDataBoundRow` obslužné rutiny události zkontrolujte, zda zadaný stáří spadá do přijatelný rozsah.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> s názvem `list1` na listu, ve kterém se zobrazí tento kód.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Postupy: sloupců objektu ListObject mapy k datům](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  