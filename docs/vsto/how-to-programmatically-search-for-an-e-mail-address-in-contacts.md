---
title: Programové hledání e-mailové adresy v kontaktech
description: Zjistěte, jak můžete pomocí sady Visual Studio programově najít e-mailovou adresu v kontaktech aplikace Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43baafee82cf38dfd346ebe50e9b348857a3fdc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920463"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Postupy: hledání e-mailových adres v kontaktech prostřednictvím kódu programu
  Tento příklad vyhledá ve složce kontaktů kontakty, které mají název domény **example.com** ve svých e-mailových adresách.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Kontakty, které mají název domény **example.com** ve svých e-mailových adresách (například `somebody@example.com` ) a mají křestní jména a příjmení.

## <a name="see-also"></a>Viz také
- [Práce s položkami kontaktů](../vsto/working-with-contact-items.md)
- [Postupy: odesílání e-mailů prostřednictvím kódu programu](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Postupy: přístup ke kontaktům aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Postupy: Přidání položky do kontaktů aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
