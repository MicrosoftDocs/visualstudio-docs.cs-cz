---
title: 'Postupy: ukládání příloh položek e-mailu aplikace Outlook prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd564b71622ad5f9ee6500ddc3864bad0b21686b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675899"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Postupy: ukládání příloh položek e-mailu aplikace Outlook prostřednictvím kódu programu
  V tomto příkladu se uloží přílohy e-mailů do zadané složky při přijetí e-mailu v doručené poště.  
  
> [!IMPORTANT]  
>  Tento příklad funguje pouze v případě, že přidáte složku s názvem **TestFileSave** v kořenovém adresáři.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s položkami pošty](../vsto/working-with-mail-items.md)   
 [Postupy: Programová načítání složek podle názvu](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Postupy: programově provádění akcí po přijetí e-mailovou zprávu](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  