---
title: 'Postupy: připojování souborů k položkám e-mailů aplikace Outlook prostřednictvím kódu programu'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2427ffc634976462e27eb788259184ce69347769
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585324"
---
# <a name="how-to-programmatically-attach-files-to-outlook-email-items"></a>Postupy: připojování souborů k položkám e-mailů aplikace Outlook prostřednictvím kódu programu
  Tento příklad připojí soubor k nové položce pošty a odešle ji do Armando Pinto. Příklad předpokládá, že jako příjemce existuje osoba s názvem Armando Pinto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_AttachFiles/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_AttachFiles/thisaddin.vb#1)]

## <a name="see-also"></a>Viz také
- [Práce s položkami pošty](../vsto/working-with-mail-items.md)
- [Postupy: odesílání e-mailů prostřednictvím kódu programu](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Postupy: ukládání příloh z e-mailových položek Outlooku prostřednictvím kódu programu](../vsto/how-to-programmatically-save-attachments-from-outlook-e-mail-items.md)
- [Postupy: vytváření položek e-mailu prostřednictvím kódu programu](../vsto/how-to-programmatically-create-an-e-mail-item.md)
