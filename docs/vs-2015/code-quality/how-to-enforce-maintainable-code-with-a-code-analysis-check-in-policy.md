---
title: 'Postupy: vykonání udržovatelného kódu se zásadou vrácení se změnami analýzy kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660223"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Postupy: Vynucování udržovatelného kódu pomocí zásady vracení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývojáři mohou použít nástroj metriky kódu k měření složitosti a udržovatelnosti kódu, ale nemohou vyvolat metriky kódu jako součást zásady vracení zpět se změnami. Tým však může povolit pravidla analýzy kódu, která ověřují dodržování předpisů kódu pomocí standardů metrik kódu a vynutila pravidla pomocí zásad vracení se změnami. Další informace o metrikách kódu naleznete v tématu [hodnoty metrik kódu](../code-quality/code-metrics-values.md).

 Vývojáři mohou povolit hloubku dědičnosti, párování tříd, indexu udržovatelnosti a pravidel složitosti, aby vynutily udržovatelnější kód prostřednictvím zásad vrácení se změnami analýzy kódu. Všechna čtyři tato pravidla se nacházejí v kategorii pravidla udržování v editoru zásad analýzy kódu.

 Správci správy verzí pro [!INCLUDE[esprfound](../includes/esprfound-md.md)] můžou do požadavků zásad vracení se změnami přidat pravidla zachování kódu. Tyto zásady vracení se změnami vyžadují, aby vývojáři před zahájením vrácení se změnami spustili analýzu kódu na základě těchto změn pravidel.

### <a name="to-open-the-code-analysis-policy-editor"></a>Otevření editoru zásad analýzy kódu

1. V **Team Explorer**klikněte pravým tlačítkem myši na týmový projekt, klikněte na položku **nastavení týmového projektu**a poté klikněte na možnost **Správa zdrojového kódu**.

     Zobrazí se dialogové okno **Správa zdrojového kódu** .

2. Na kartě **Zásady vracení se změnami** klikněte na **Přidat**.

     Zobrazí se dialogové okno **Přidat zásadu vrácení se změnami** .

3. V seznamu **Zásady vracení se změnami** zaškrtněte políčko **Analýza kódu** a pak klikněte na tlačítko **OK**.

     Zobrazí se dialogové okno **Editor zásad analýzy kódu** .

### <a name="to-enable-code-analysis-maintainability-rules"></a>Povolení pravidel zachování analýzy kódu

1. V dialogovém okně **Editor zásad analýzy kódu** v části **Nastavení pravidla**rozbalte uzel **pravidla udržovatelnosti** .

2. Zaškrtněte políčka pro následující pravidla:

    - Hloubka dědičnosti: **CA1501 AvoidExcessiveInheritance** – prahová hodnota: upozornění na více než 5 úrovních hluboko

    - Složitost: **CA1502 AvoidExcessiveComplexity** – prahová hodnota: upozornění na více než 25

    - Index udržovatelnosti: **CA1505 AvoidUnmaintainableCode** – prahová hodnota: upozornění s méně než 20

    - Párování tříd: **CA1506 AvoidExcessiveClassCoupling** – prahová hodnota: upozornění na více než 80 pro třídu a více než 30 pro metodu

    - Kromě toho, pokud chcete, aby bylo porušení pravidla zabráněno sestavení, zaškrtněte políčko **považovat upozornění jako chybu** vedle popisu pravidla.

3. Klikněte na tlačítko **OK**. Nové zásady vracení se změnami se teď vztahují na budoucí vrácení se změnami.

## <a name="see-also"></a>Viz také
 [Hodnoty metrik kódu](../code-quality/code-metrics-values.md) [vytváření a používání zásad vrácení se změnami analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
