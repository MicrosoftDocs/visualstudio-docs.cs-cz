---
title: 'Krok 9: Vyzkoušejte další funkce'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ac2f1977bb0b8b391651ed7ed459b9dc560330
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579730"
---
# <a name="step-9-try-other-features"></a>Krok 9: Vyzkoušejte další funkce
Chcete-li získat další informace, zkuste změnit ikony a barvy, přidat časovač hry a zvuky. Chcete-li, aby hra byla náročnější, zkuste zvětšit hrací plochu a upravte časovač.

Pokud chcete stáhnout dokončenou verzi ukázky, přečtěte si část [Kompletní odpovídající ukázka výukového programu pro hru](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí

- Nahraďte ikony a barvy těmi, které zvolíte.

    > [!TIP]
    > Zkuste se podívat na vlastnost [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) štítku.

- Přidejte časovač hry, který sleduje, jak dlouho hráči trvá, než vyhraje.

    > [!TIP]
    > Chcete-li to provést, můžete přidat popisek pro zobrazení uplynulého času ve formuláři nad písmenem <xref:System.Windows.Forms.TableLayoutPanel>a) a přidáním dalšího časovače do formuláře ke sledování času. Použijte kód ke spuštění časovače, když hráč zahájí hru, a zastavení časovače, jakmile hráč spojí poslední dvě ikony.

- Pokud hráč najde shodu, přidejte zvuk, jiný zvuk, když hráč odkryje dvě ikony, které neodpovídají, a třetí zvuk, když program znovu skryje ikony.

    > [!TIP]
    > Chcete-li přehrávat zvuky, můžete použít obor <xref:System.Media> názvů. Další informace najdete v tématech [Přehrávání zvuků v aplikaci Pro Windows Forms (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) nebo [Jak přehrávat zvuk v jazyce Visual Basic.](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be)

- Udělejte hru obtížnější tím, že zvětšíte hrací plochu.

    > [!TIP]
    > Budete muset udělat víc, než jen přidat řádky a sloupce tablelayoutpanel - budete také muset vzít v úvahu počet ikon, které vytvoříte.

- Udělejte hru náročnější tím, že skryjete první ikonu, pokud je hráč příliš pomalý a nezvolí druhou ikonu do vypršení určitého časového limitu.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- K dispozici jsou užitečné bezplatné video výukové materiály. Další informace o programování v jazyce Visual Basic najdete v [tématu Základy jazyka: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v jazyce C#, viz [Základy jazyka C#: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si postup 8: Přidání metody k ověření, zda hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
