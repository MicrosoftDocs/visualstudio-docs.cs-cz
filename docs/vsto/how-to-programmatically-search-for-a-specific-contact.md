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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e163bd172b16841103641befa7e08a87d5bd0cde
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828966"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu
  Tento příklad vyhledá ve složce kontaktů Outlooku konkrétní kontakt podle jména a příjmení. V příkladu se předpokládá, že ve složce kontaktů existuje kontakt s názvem **Jan Evans** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb" id="Snippet1":::

## <a name="see-also"></a>Viz také
- [Práce s položkami kontaktů](../vsto/working-with-contact-items.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
