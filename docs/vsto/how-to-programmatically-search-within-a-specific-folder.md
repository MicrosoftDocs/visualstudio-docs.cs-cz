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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824754"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu
  Tento příklad kódu používá `Find` metody a `FindNext` k hledání textu v poli subjekt e-mailových zpráv, které jsou ve **složce Doručená pošta**. Tato metoda používá filtr řetězce pro kontrolu písmene T jako počáteční písmeno `Subject` textu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
