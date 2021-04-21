---
title: Ukládat přílohy z e-mailových položek Outlooku programově
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově ukládat přílohy z e-mailových položek aplikace Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ad64593f91e14bcfd993929420764869a8359e3e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826691"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Postupy: ukládání příloh z e-mailových položek Outlooku prostřednictvím kódu programu

Tento příklad uloží přílohy e-mailu do zadané složky, když se e-mail obdrží v doručené poště.

> [!IMPORTANT]
> Tento příklad funguje pouze v případě, že do kořene adresáře C přidáte složku s názvem **TestFileSave** .

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Viz také

- [Práce s položkami pošty](../vsto/working-with-mail-items.md)
- [Postupy: načítání složek podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Postupy: provádění akcí po přijetí e-mailové zprávy prostřednictvím kódu programu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
