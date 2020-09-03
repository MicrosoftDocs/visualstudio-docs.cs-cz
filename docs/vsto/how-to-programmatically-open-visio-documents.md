---
title: 'Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb21d201c282461cbe82005f56bed023bb022209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519987"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu
  Existují dvě metody otevření existujících systém Microsoft Office dokumentů aplikace Visio: Open a OpenEx. Metoda OpenEx je shodná s metodou Open, s tím rozdílem, že poskytuje argumenty, ve kterých může volající určit způsob otevření dokumentu.

 Podrobnosti o objektovém modelu naleznete v referenční dokumentaci jazyka VBA pro [Microsoft.Office.Interop.Visio.Documents. Otevřete](/office/vba/api/Visio.Documents.Open) metodu a [Microsoft.Office.Interop.Visio.Documents. OpenEx](/office/vba/api/Visio.Documents.OpenEx) – metoda

## <a name="open-a-visio-document"></a>Otevření dokumentu Visia

### <a name="to-open-a-visio-document"></a>Otevření dokumentu aplikace Visio

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.Open` metodu a zadejte plně kvalifikovanou cestu k dokumentu Visia.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Otevřít dokument Visia se zadanými argumenty

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Otevření dokumentu aplikace Visio jako jen pro čtení a ukotven

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.OpenEx` metodu, zadejte plně kvalifikovanou cestu k dokumentu aplikace Visio a zahrňte argumenty, které chcete použít – v tomto případě ukotvené a jen pro čtení.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu vyžaduje následující:

- Dokument aplikace Visio s názvem `myDrawing.vsd` musí být umístěn v adresáři s názvem `Test` ve složce *dokumenty* (pro systém Windows XP a starší) nebo ve složce *dokumenty* (pro systém Windows Vista).

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)
- [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)
- [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)
