---
title: Ukládat do mezipaměti zdroj dat v dokumentu Office prostřednictvím kódu programu
description: Přečtěte si, jak programově přidat datový objekt do mezipaměti dat v dokumentu voláním metody StartCaching položky hostitele.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070253fb7ec57bedad628e116ce193fa2d9cf50b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827588"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Postupy: ukládání zdroje dat v dokumentu Office do mezipaměti prostřednictvím kódu programu
  Můžete programově přidat datový objekt do mezipaměti dat v dokumentu voláním `StartCaching` metody hostitelské položky, například <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet> . Odstraňte datový objekt z mezipaměti dat voláním `StopCaching` metody hostitelské položky.

 `StartCaching`Metoda a `StopCaching` Metoda jsou oba soukromé, ale zobrazují se v IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Při použití `StartCaching` metody k přidání datového objektu do mezipaměti dat není nutné datový objekt deklarovat s <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributem. Datový objekt však musí splňovat určité požadavky, které mají být přidány do mezipaměti dat. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Programové ukládání datového objektu do mezipaměti

1. Deklarujte datový objekt na úrovni třídy, ne uvnitř metody. Tento příklad předpokládá, že deklarujete <xref:System.Data.DataSet> název `dataSet1` , který chcete ukládat do mezipaměti prostřednictvím kódu programu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Vytvořte instanci datového objektu a potom zavolejte `StartCaching` metodu instance dokumentu nebo listu a předejte název datového objektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Zastavení ukládání datového objektu do mezipaměti

1. Zavolejte `StopCaching` metodu instance dokumentu nebo listu a předejte název datového objektu. V tomto příkladu se předpokládá, že máte <xref:System.Data.DataSet> s názvem `dataSet1` , který chcete zastavit ukládání do mezipaměti.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > Nevolejte `StopCaching` z obslužné rutiny události pro `Shutdown` událost dokumentu nebo listu. V době, kdy je `Shutdown` událost vyvolána, je příliš pozdě měnit mezipaměť dat. Další informace o `Shutdown` události najdete [v tématu události v projektech Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Viz také

- [Data mezipaměti](../vsto/caching-data.md)
- [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md)
- [Ukládání dat](../data-tools/save-data-back-to-the-database.md)
