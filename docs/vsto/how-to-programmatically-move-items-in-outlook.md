---
title: 'Postupy: přesouvání položek v aplikaci Outlook prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257719"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Postupy: přesouvání položek v aplikaci Outlook prostřednictvím kódu programu
  Tento příklad přesune nepřečtené e-mailové zprávy z **doručené pošty** do složky s názvem **Test**. V příkladu přesouvá pouze zprávy, které mají slovo **Test** v `Subject` pole.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Složky aplikace Outlook e-mailu s názvem **Test**.  
  
-   E-mailovou zprávu, která dorazí slovem **Test** v `Subject` pole.  
  
## <a name="see-also"></a>Viz také:  
 [Práce se složkami](../vsto/working-with-folders.md)   
 [Postupy: načítání do složky podle názvu prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Postupy: programové provádění akcí po přijetí e-mailovou zprávu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  