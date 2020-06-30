---
title: 'Postupy: vytváření vlastních kalendářů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom calendars [Office development in Visual Studio]
- calendars [Office development in Visual Studio], custom
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aab9e14c7fa4b4c70b2e61eca382af2ce787148c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546052"
---
# <a name="how-to-programmatically-create-a-custom-calendar"></a>Postupy: vytváření vlastních kalendářů prostřednictvím kódu programu
  Tento příklad vytvoří novou složku kalendáře s názvem **PersonalCalendar**a potom vytvoří novou položku události a přidá ji do složky kalendáře. Kód pak zobrazí složku kalendáře.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_OL_CustomCalendar#1](../vsto/codesnippet/CSharp/Trin_OL_CustomCalendar/thisaddin.cs#1)]

## <a name="see-also"></a>Viz také
- [Práce s položkami kalendáře](../vsto/working-with-calendar-items.md)
- [Postupy: vytváření událostí prostřednictvím kódu programu](../vsto/how-to-programmatically-create-appointments.md)
- [Postupy: vytváření žádostí o schůzku prostřednictvím kódu programu](../vsto/how-to-programmatically-create-a-meeting-request.md)
