---
title: Použít zásadu vrácení se změnami analýzy kódu
ms.date: 11/04/2016
description: Naučte se používat zásadu vrácení se změnami analýzy kódu k ověření, že kód vyhovuje dědičnosti, párování tříd, údržbě a standardům složitosti.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fa97f52f67e08b2ccf0843e5b5400680ed1c020
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434815"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Postupy: vykonání udržovatelného kódu se zásadou vrácení se změnami analýzy kódu

Vývojáři mohou použít nástroj metriky kódu k měření složitosti a udržovatelnosti kódu, ale nelze vyvolat metriky kódu jako součást zásady vracení zpět se změnami. Můžete však povolit pravidla analýzy kódu, která ověřují dodržování předpisů v kódu pomocí standardů metrik kódu a vynutila pravidla pomocí zásad vracení se změnami. Další informace o metrikách kódu naleznete v tématu [hodnoty metrik kódu](../code-quality/code-metrics-values.md).

Můžete povolit hloubku dědičnosti, párování tříd, indexu udržovatelnosti a pravidel složitosti k zajištění udržovatelného kódu prostřednictvím zásad vrácení se změnami analýzy kódu. Všechna čtyři tato pravidla se nacházejí v kategorii pravidla udržování v editoru zásad analýzy kódu.

Správci správy verzí pro Team Foundation můžou do požadavků zásad vracení se změnami přidat pravidla zachování kódu. Tyto zásady vracení se změnami vyžadují, aby vývojáři před zahájením vrácení se změnami spustili analýzu kódu na základě těchto změn pravidel.

## <a name="to-open-the-code-analysis-policy-editor"></a>Otevření editoru zásad analýzy kódu

1. V **Team Explorer** klikněte pravým tlačítkem myši na projekt, klikněte na **nastavení projektu** a pak klikněte na **Správa zdrojového kódu**.

     Zobrazí se dialogové okno **Správa zdrojového kódu** .

2. Na kartě **Zásady vracení se změnami** klikněte na **Přidat**.

     Zobrazí se dialogové okno **Přidat zásadu vrácení se změnami** .

3. V seznamu **Zásady vracení se změnami** zaškrtněte políčko **Analýza kódu** a pak klikněte na tlačítko **OK**.

     Zobrazí se dialogové okno **Editor zásad analýzy kódu** .

## <a name="to-enable-code-analysis-maintainability-rules"></a>Povolení pravidel zachování analýzy kódu

1. V dialogovém okně **Editor zásad analýzy kódu** v části **Nastavení pravidla** rozbalte uzel **pravidla udržovatelnosti** .

2. Zaškrtněte políčka pro následující pravidla:

   - Hloubka dědičnosti: **CA1501 AvoidExcessiveInheritance** – prahová hodnota: upozornění na více než 5 úrovních hluboko

   - Složitost: **CA1502 AvoidExcessiveComplexity** – prahová hodnota: upozornění na více než 25

   - Index udržovatelnosti: **CA1505 AvoidUnmaintainableCode** – prahová hodnota: upozornění s méně než 20

   - Párování tříd: **CA1506 AvoidExcessiveClassCoupling** – prahová hodnota: upozornění na více než 80 pro třídu a více než 30 pro metodu

     Pokud navíc chcete, aby porušení pravidla zabránilo úspěšnému sestavení, zaškrtněte políčko **považovat upozornění jako chybu** vedle popisu pravidla.

3. Klikněte na **OK**. Nové zásady vracení se změnami se teď vztahují na budoucí vrácení se změnami.

## <a name="see-also"></a>Viz také

- [Hodnoty metrik kódu](../code-quality/code-metrics-values.md)
- [Vytváření a používání zásad vrácení se změnami analýzy kódu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
