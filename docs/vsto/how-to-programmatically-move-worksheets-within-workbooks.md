---
title: 'Postupy: přesouvání listů v sešitech prostřednictvím kódu programu'
description: Naučte se programově měnit pozici listů relativně k ostatním listům v sešitu Microsoft Excelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827289"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Postupy: přesouvání listů v sešitech prostřednictvím kódu programu
  Můžete programově měnit pozici listů relativně k ostatním listům v sešitu. Pokud nezadáte umístění pro přesunutý list, aplikace Excel vytvoří nový sešit, který bude obsahovat.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Přesunutí listu v přizpůsobení na úrovni dokumentu

1. Přiřaďte celkový počet listů v sešitu proměnné a pak přesuňte první list tak, aby se stal jeho posledním.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Přesunutí listu v doplňku VSTO

1. Přiřaďte celkový počet listů v sešitu proměnné a pak přesuňte první list tak, aby se stal jeho posledním.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
