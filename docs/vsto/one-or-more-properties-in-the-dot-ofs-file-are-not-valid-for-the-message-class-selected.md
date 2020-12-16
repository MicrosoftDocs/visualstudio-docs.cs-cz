---
title: Neplatné vlastnosti v souboru. ofs pro třídu zprávy "
description: Zjistěte, jak opravit chybu, ke které dochází, pokud jedna nebo více vlastností v souboru. ofs nejsou pro vybranou třídu zpráv platné.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b655a7bb6ab4b9ab971c0edd775aa8f29150dead
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525087"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Neplatné vlastnosti v souboru. ofs pro třídu Message

  Chyba "jedna nebo více vlastností v souboru. ofs nejsou pro vybranou třídu zpráv platné" zobrazí se při importu oblasti formuláře, která je navržena v aplikaci Outlook, ale nejméně jedno pole v oblasti formuláře není kompatibilní s třídami zpráv, které jste vybrali na poslední stránce Průvodce vytvořením **nové oblasti formuláře** .

Můžete například vybrat **úlohu (IPM. Úkol)** na poslední stránce Průvodce vytvořením **nové oblasti formuláře** . Pokud oblast formuláře má pole **obchodní adresa** , zobrazí se tato chyba, protože úkol nemá obchodní adresu. Proto pole **obchodní adresa** není kompatibilní s `IPM.Task` třídou Message.

 Můžete vybrat **úlohu (IPM. Úkol)** na poslední stránce Průvodce vytvořením **nové oblasti formuláře** . Pokud oblast formuláře má pole **obchodní adresa** , zobrazí se tato chyba, protože úkol nemá obchodní adresu. Proto pole **obchodní adresa** není kompatibilní s `IPM.Task` třídou Message.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Na poslední stránce Průvodce vytvořením **oblasti formuláře** vyberte třídu zprávy, která je kompatibilní s poli v oblasti formuláře.

- V Návrháři formulářů v aplikaci Outlook odeberte pole, která nejsou kompatibilní s třídami zpráv. Na poslední stránce Průvodce vytvořením **oblasti formuláře** odeberte pole, která chcete vybrat.

## <a name="see-also"></a>Viz také
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
