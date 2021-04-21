---
title: 'Postupy: přístup ke kontaktům aplikace Outlook prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově přistupovat ke kontaktům aplikace Outlook. Tento příklad vyhledá všechny kontakty, jejichž příjmení obsahují zadaný hledaný řetězec.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828901"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Postupy: přístup ke kontaktům aplikace Outlook prostřednictvím kódu programu
  Tento příklad vyhledá všechny kontakty, jejichž příjmení obsahují zadaný hledaný řetězec.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Kontakty, jejichž příjmení obsahují řetězec "**NEDEF"** (například Tzipi Butnaru) ve složce **kontaktů** .

## <a name="see-also"></a>Viz také
- [Práce s položkami kontaktů](../vsto/working-with-contact-items.md)
- [Postupy: Přidání položky do kontaktů aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Postupy: hledání e-mailových adres v kontaktech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Postupy: odstraňování kontaktů aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-outlook-contacts.md)
