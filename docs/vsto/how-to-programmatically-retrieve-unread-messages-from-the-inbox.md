---
title: Programově načíst nepřečtené zprávy z doručené pošty
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově načíst nepřečtené zprávy z vaší doručené pošty v aplikaci Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6dae629c008c04f7ee9fb66b9dbc5f8f31e53d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528259"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Postupy: načítání nepřečtených zpráv z doručené pošty prostřednictvím kódu programu
  Tento příklad načte nepřečtené e-mailové zprávy z **doručené pošty** Outlooku a zobrazí počet položek.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce s položkami pošty](../vsto/working-with-mail-items.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Postupy: vytváření položek e-mailu prostřednictvím kódu programu](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Postupy: odesílání e-mailů prostřednictvím kódu programu](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Postupy: provádění akcí po přijetí e-mailové zprávy prostřednictvím kódu programu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
