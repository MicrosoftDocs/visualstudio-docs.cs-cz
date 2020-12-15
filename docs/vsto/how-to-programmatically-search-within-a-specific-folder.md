---
title: 'Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu'
description: Zjistěte, jak můžete pomocí sady Visual Studio programově vyhledávat v rámci konkrétní složky Microsoft Outlooku.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524538"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu
  Tento příklad kódu používá `Find` metody a `FindNext` k hledání textu v poli subjekt e-mailových zpráv, které jsou ve **složce Doručená pošta**. Tato metoda používá filtr řetězce pro kontrolu písmene T jako počáteční písmeno `Subject` textu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
