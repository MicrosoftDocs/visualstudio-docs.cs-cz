---
title: 'Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu'
description: Zjistěte, jak můžete pomocí sady Visual Studio programově vyhledat konkrétní kontakt v aplikaci Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524612"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu
  Tento příklad vyhledá ve složce kontaktů Outlooku konkrétní kontakt podle jména a příjmení. V příkladu se předpokládá, že ve složce kontaktů existuje kontakt s názvem **Jan Evans** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Viz také
- [Práce s položkami kontaktů](../vsto/working-with-contact-items.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
