---
title: 'Postupy: přesouvání položek v aplikaci Outlook prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově přesouvat položky v aplikaci Microsoft Outlook. Tento příklad přesune nepřečtené e-mailové zprávy z doručené pošty do složky s názvem test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888859"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Postupy: přesouvání položek v aplikaci Outlook prostřednictvím kódu programu
  Tento příklad přesune nepřečtené e-mailové zprávy z **doručené pošty** do složky s názvem **test**. V příkladu se do pole přesune pouze zprávy, které mají slovo **test** `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Poštovní složka Outlooku s názvem **test**.

- E-mailová zpráva, která dorazí na slovo **test** v `Subject` poli.

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Postupy: provádění akcí po přijetí e-mailové zprávy prostřednictvím kódu programu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
