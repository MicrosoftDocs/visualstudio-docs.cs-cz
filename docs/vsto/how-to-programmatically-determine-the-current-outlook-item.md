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
ms.openlocfilehash: 720028528c036bf4485ca529f735fd26b1ff6e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963832"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Postupy: určení aktuální položky aplikace Outlook prostřednictvím kódu programu
  V tomto příkladu se používá `Explorer.SelectionChange` událost k zobrazení názvu aktuální složky a některých informací o vybrané položce. Kód pak zobrazí vybranou položku.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Položky schůzka, kontakt a e-mail v aplikaci systém Microsoft Office Outlook.

## <a name="see-also"></a>Viz také
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
