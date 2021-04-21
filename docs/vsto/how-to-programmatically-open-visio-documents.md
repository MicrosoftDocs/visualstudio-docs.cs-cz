---
title: 'Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově otevřít dokument Visia pomocí metod Open nebo OpenEx.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f96efd41eb91551fe3cf7c03b55a44b7a9e1bf1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824741"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu
  Existují dvě metody otevření existujících systém Microsoft Office dokumentů aplikace Visio: Open a OpenEx. Metoda OpenEx je shodná s metodou Open, s tím rozdílem, že poskytuje argumenty, ve kterých může volající určit způsob otevření dokumentu.

 Podrobnosti o objektovém modelu naleznete v referenční dokumentaci jazyka VBA pro [Microsoft.Office.Interop.Visio.Documents. Otevřete](/office/vba/api/Visio.Documents.Open) metodu a [Microsoft.Office.Interop.Visio.Documents. OpenEx](/office/vba/api/Visio.Documents.OpenEx) – metoda

## <a name="open-a-visio-document"></a>Otevření dokumentu Visia

### <a name="to-open-a-visio-document"></a>Otevření dokumentu aplikace Visio

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.Open` metodu a zadejte plně kvalifikovanou cestu k dokumentu Visia.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Otevřít dokument Visia se zadanými argumenty

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Otevření dokumentu aplikace Visio jako jen pro čtení a ukotven

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.OpenEx` metodu, zadejte plně kvalifikovanou cestu k dokumentu aplikace Visio a zahrňte argumenty, které chcete použít – v tomto případě ukotvené a jen pro čtení.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

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
