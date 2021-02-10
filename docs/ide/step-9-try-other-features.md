---
title: 'Krok 9: Vyzkoušení dalších funkcí'
description: Naučte se, jak změnit ikony a barvy, Přidat časovač her, přidat zvuky a zvětšit herní panel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e405cef9360083a8f0169ac338e2c23cffc71218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969552"
---
# <a name="step-9-try-other-features"></a>Krok 9: Vyzkoušení dalších funkcí
Chcete-li získat další informace, zkuste změnit ikony a barvy, přidat časovač hry a zvuky. Chcete-li, aby hra byla náročnější, zkuste zvětšit hrací plochu a upravte časovač.

Pokud si chcete stáhnout dokončenou verzi ukázky, přečtěte si [ukázku s kurzem kompletní porovnávací hru](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí

- Nahraďte ikony a barvy těmi, které zvolíte.

    > [!TIP]
    > Zkuste se podívat na vlastnost [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) popisku.

- Přidejte časovač hry, který sleduje, jak dlouho hráči trvá, než vyhraje.

    > [!TIP]
    > K tomu můžete přidat popisek pro zobrazení uplynulého času ve formuláři nad a <xref:System.Windows.Forms.TableLayoutPanel> Přidat další časovač pro sledování času. Použijte kód ke spuštění časovače, když hráč zahájí hru, a zastavení časovače, jakmile hráč spojí poslední dvě ikony.

- Pokud hráč najde shodu, přidejte zvuk, jiný zvuk, když hráč odkryje dvě ikony, které neodpovídají, a třetí zvuk, když program znovu skryje ikony.

    > [!TIP]
    > Chcete-li přehrát zvuky, můžete použít <xref:System.Media> obor názvů. Další informace najdete v tématu [přehrání zvuku v model Windows Forms App (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) nebo [přehrání zvuku v Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) .

- Udělejte hru obtížnější tím, že zvětšíte hrací plochu.

    > [!TIP]
    > Budete muset udělat více než jenom přidat řádky a sloupce do kontejneru TableLayoutPanel – budete taky muset vzít v úvahu počet ikon, které vytvoříte.

- Udělejte hru náročnější tím, že skryjete první ikonu, pokud je hráč příliš pomalý a nezvolí druhou ikonu do vypršení určitého časového limitu.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- K dispozici jsou užitečné bezplatné video výukové materiály. Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v jazyce C# najdete v tématu [základy jazyka c#: vývoj pro naprostou začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 8: Přidání metody pro ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
