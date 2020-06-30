---
title: 'Postupy: načítání složek podle názvu prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 901de848b22f344ded2d71b11e9859917b8382d4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547105"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Postupy: načítání složek podle názvu prostřednictvím kódu programu
  Tento příklad získá odkaz na pojmenovanou vlastní složku a pak zobrazí obsah složky.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Složka s názvem TestFolder.

## <a name="see-also"></a>Viz také
- [Práce se složkami](../vsto/working-with-folders.md)
- [Postupy: hledání v rámci konkrétní složky prostřednictvím kódu programu](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Postupy: vytváření vlastních položek složek prostřednictvím kódu programu](../vsto/how-to-programmatically-create-custom-folder-items.md)
