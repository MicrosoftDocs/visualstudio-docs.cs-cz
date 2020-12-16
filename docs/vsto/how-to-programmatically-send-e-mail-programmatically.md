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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f31fdb92a5acff16b1d6e8001ea88931a9a22ab
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525373"
---
# <a name="how-to-programmatically-send-email"></a>Postupy: odesílání e-mailů prostřednictvím kódu programu
  Tento příklad pošle e-mailovou zprávu kontaktům, které mají název domény **example.com** ve svých e-mailových adresách.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

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
