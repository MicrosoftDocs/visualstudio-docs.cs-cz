---
title: Přidružení webové stránky ke složce aplikace Outlook
description: Přečtěte si, jak můžete přidružit webovou stránku ke složce systém Microsoft Office Outlooku. Tento příklad kontroluje složku s názvem HtmlView v aplikaci Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885570"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Přidružení webové stránky ke složce aplikace Outlook

  Tento příklad kontroluje složku s názvem `HtmlView` v systém Microsoft Office Outlook. Pokud složka neexistuje, kód vytvoří složku a přiřadí jí webovou stránku. Pokud složka existuje, kód zobrazí obsah složky.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Postupy: vytváření vlastních položek složek prostřednictvím kódu programu](../vsto/how-to-programmatically-create-custom-folder-items.md)
