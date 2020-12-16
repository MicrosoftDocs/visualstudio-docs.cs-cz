---
title: 'Postupy: vytváření vlastních položek složek prostřednictvím kódu programu'
description: Přečtěte si, jak programově vytvářet vlastní položky složek v Microsoft Outlooku pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: f149758665e5d7a7cdf7f4edd5d926e1de632dca
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527787"
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>Postupy: vytváření vlastních položek složek prostřednictvím kódu programu
  Tento příklad vytvoří novou složku v aplikaci systém Microsoft Office Outlook. Pro název složky se používá jméno přihlášeného uživatele.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Postupy: Přidání položky do kontaktů aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Postupy: vytváření událostí prostřednictvím kódu programu](../vsto/how-to-programmatically-create-appointments.md)
