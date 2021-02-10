---
title: 'Postupy: odstraňování kontaktů aplikace Outlook prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově odstraňovat kontakty v aplikaci Microsoft Outlook. Tento příklad odstraní jeden kontakt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deleting contacts
- contacts [Office development in Visual Studio], deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 98ee7773c86e85fa9ced0274bc37c4db3f8aacc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963888"
---
# <a name="how-to-programmatically-delete-outlook-contacts"></a>Postupy: odstraňování kontaktů aplikace Outlook prostřednictvím kódu programu
  Tento příklad odstraní kontakt. V příkladu se předpokládá, že ve složce **kontaktů** existuje kontakt s názvem "Armando Pinto".

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-vb[Trin_Outlook_RL_DeleteContacts#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_DeleteContacts/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_DeleteContacts#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_DeleteContacts/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce s položkami kontaktů](../vsto/working-with-contact-items.md)
- [Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Postupy: přístup ke kontaktům aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-access-outlook-contacts.md)
