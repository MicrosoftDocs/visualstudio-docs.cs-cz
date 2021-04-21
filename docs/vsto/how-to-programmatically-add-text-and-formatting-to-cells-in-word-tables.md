---
title: Přidání textu &ho formátování do buněk tabulky aplikace Word prostřednictvím kódu programu
description: Přečtěte si, jak můžete programově přidávat text a formátování do buněk v systém Microsoft Office tabulky Wordu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 58c9e7f7d5537e4b052a732a85ad9d1c7298afa0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828394"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Postupy: přidávání textu a formátování do buněk v tabulkách aplikace Word prostřednictvím kódu programu
  Každá tabulka se skládá z kolekce buněk. Každý jednotlivý <xref:Microsoft.Office.Interop.Word.Cell> objekt představuje jednu buňku v tabulce. Na každou buňku odkazujete podle jejího umístění v tabulce. Tento příklad odkazuje na buňku umístěnou v prvním řádku a prvním sloupci v tabulce. Přidá text do buňky. a aplikuje formátování.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Přidání textu a formátování do buněk

1. Podívejte se na buňku podle jejího umístění v tabulce, přidejte text do buňky a použijte formátování.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu. Chcete-li použít tento příklad, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument. Chcete-li použít příklad, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>Viz také
- [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-create-word-tables.md)
- [Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Postupy: naplnění tabulek Wordu pomocí vlastností dokumentu prostřednictvím kódu programu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
