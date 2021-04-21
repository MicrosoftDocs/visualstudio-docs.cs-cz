---
title: 'Postupy: odesílání e-mailů prostřednictvím kódu programu'
description: Pomocí sady Visual Studio programově odešlete e-mail z aplikace Microsoft Outlook. Tento příklad pošle e-mailovou zprávu kontaktům, které mají název domény example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fa6a45a199d4edce924f0e36a971026726d96eca
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824793"
---
# <a name="how-to-programmatically-send-email"></a>Postupy: odesílání e-mailů prostřednictvím kódu programu
  Tento příklad pošle e-mailovou zprávu kontaktům, které mají název domény **example.com** ve svých e-mailových adresách.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Kontakty, které mají název domény **example.com** ve svých e-mailových adresách.

## <a name="robust-programming"></a>Robustní programování
 Neodstraňujte kód filtru, který vyhledává název domény **example.com**. Pokud filtr odeberete, vaše řešení pošle e-mailové zprávy všem vašim kontaktům.

## <a name="see-also"></a>Viz také
- [Práce s položkami pošty](../vsto/working-with-mail-items.md)
- [Postupy: vytváření položek e-mailu prostřednictvím kódu programu](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Postupy: přístup ke kontaktům aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Postupy: provádění akcí po přijetí e-mailové zprávy prostřednictvím kódu programu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
