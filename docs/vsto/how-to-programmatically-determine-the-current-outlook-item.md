---
title: 'Postupy: určení aktuální položky aplikace Outlook prostřednictvím kódu programu'
description: Zjistěte, jak programově určit aktuální položku aplikace Microsoft Outlook. V tomto příkladu se používá událost Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cddc4bdc99e97c12a04e57639f990a1484c6581
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823917"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Postupy: určení aktuální položky aplikace Outlook prostřednictvím kódu programu
  V tomto příkladu se používá `Explorer.SelectionChange` událost k zobrazení názvu aktuální složky a některých informací o vybrané položce. Kód pak zobrazí vybranou položku.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Položky schůzka, kontakt a e-mail v aplikaci systém Microsoft Office Outlook.

## <a name="see-also"></a>Viz také
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
