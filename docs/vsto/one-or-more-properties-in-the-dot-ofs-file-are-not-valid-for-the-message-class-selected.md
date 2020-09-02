---
title: Jedna nebo více vlastností v souboru .ofs nejsou pro vybranou třídu zpráv platné.
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977858"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna nebo více vlastností v souboru .ofs nejsou pro vybranou třídu zpráv platné.
  Tato chyba se zobrazí při importu oblasti formuláře, která je navržena v aplikaci Outlook, ale nejméně jedno pole v oblasti formuláře není kompatibilní s třídami zpráv, které vyberete na poslední stránce Průvodce vytvořením **nové oblasti formuláře** .

Můžete například vybrat **úlohu (IPM. Úkol)** na poslední stránce Průvodce vytvořením **nové oblasti formuláře** . Pokud oblast formuláře má pole **obchodní adresa** , zobrazí se tato chyba, protože úkol nemá obchodní adresu. Proto pole **obchodní adresa** není kompatibilní s `IPM.Task` třídou Message.

 Můžete vybrat **úlohu (IPM. Úkol)** na poslední stránce Průvodce vytvořením **nové oblasti formuláře** . Pokud oblast formuláře má pole **obchodní adresa** , zobrazí se tato chyba, protože úkol nemá obchodní adresu. Proto pole **obchodní adresa** není kompatibilní s `IPM.Task` třídou Message.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Na poslední stránce Průvodce vytvořením **oblasti formuláře** vyberte třídu zprávy, která je kompatibilní s poli v oblasti formuláře.

- V Návrháři formulářů v aplikaci Outlook odeberte pole, která nejsou kompatibilní s třídami zpráv. Na poslední stránce Průvodce vytvořením **oblasti formuláře** odeberte pole, která chcete vybrat.

## <a name="see-also"></a>Viz také
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
