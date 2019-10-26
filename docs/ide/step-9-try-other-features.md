---
title: 'Krok 9: Vyzkoušejte jiné funkce'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07c0a3e24ac089bf29501dfd4e101baef73318fb
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919139"
---
# <a name="step-9-try-other-features"></a>Krok 9: Vyzkoušejte jiné funkce
Chcete-li získat další informace, zkuste změnit ikony a barvy, přidat časovač hry a zvuky. Chcete-li, aby hra byla náročnější, zkuste zvětšit hrací plochu a upravte časovač.

Pokud si chcete stáhnout dokončenou verzi ukázky, přečtěte si [ukázku s kurzem kompletní porovnávací hru](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí

- Nahraďte ikony a barvy těmi, které zvolíte.

    > [!TIP]
    > Zkuste se podívat na vlastnost [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) popisku.

- Přidejte časovač hry, který sleduje, jak dlouho hráči trvá, než vyhraje.

    > [!TIP]
    > K tomu můžete přidat popisek, který zobrazí uplynulý čas ve formuláři nad <xref:System.Windows.Forms.TableLayoutPanel> a do formuláře přidejte další časovač, abyste mohli sledovat čas. Použijte kód ke spuštění časovače, když hráč zahájí hru, a zastavení časovače, jakmile hráč spojí poslední dvě ikony.

- Pokud hráč najde shodu, přidejte zvuk, jiný zvuk, když hráč odkryje dvě ikony, které neodpovídají, a třetí zvuk, když program znovu skryje ikony.

    > [!TIP]
    > Chcete-li přehrát zvuky, můžete použít obor názvů <xref:System.Media>. Další informace najdete v tématu [přehráníC#zvuku v aplikaci model Windows Forms App ()](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) nebo [o tom, jak přehrát zvuk v Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) .

- Udělejte hru obtížnější tím, že zvětšíte hrací plochu.

    > [!TIP]
    > Budete muset udělat více než jenom přidat řádky a sloupce do kontejneru TableLayoutPanel – budete taky muset vzít v úvahu počet ikon, které vytvoříte.

- Udělejte hru náročnější tím, že skryjete první ikonu, pokud je hráč příliš pomalý a nezvolí druhou ikonu do vypršení určitého časového limitu.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- K dispozici jsou užitečné bezplatné video výukové materiály. Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v C#nástroji najdete v tématu [ C# základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 8: Přidání metody pro ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
