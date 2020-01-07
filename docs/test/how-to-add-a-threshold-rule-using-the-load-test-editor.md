---
title: Přidat pravidlo mezní hodnoty pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1389df0c307ad6ec65575fc7934e622928a0ca1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591629"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Postupy: Přidání mezního pravidla pomocí editoru zátěžových testů

Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Chcete-li přidat mezní pravidlo:

1. Otevřete zátěžový test.

2. V editoru zátěžového testu rozbalte **sady čítačů** uzlu.

3. Rozbalte některou **kategorie čítačů** v jedné ze sad čítačů. Například můžete vybrat **loadtest: Scenario**. Rozbalte uzel.

4. Klikněte pravým tlačítkem z čítačů, například **uživatelské zatížení**v části **loadtest: Scenario**. Vyberte **přidat pravidlo mezní hodnoty**.

     **Přidat pravidlo mezní hodnoty** se zobrazí dialogové okno.

5. Můžete vybrat ze dvou typů pravidel: **konstanta porovnání** a **čítač porovnání**. Vyberte požadovaný typ a nastavte hodnoty.

    > [!NOTE]
    > Nastavte **upozornění, pokud přesáhne** vlastnost **True** k označení, že překročení mezní hodnoty je nějaký problém nebo **False** označuje, že snížení pod mezní hodnotu k problému.

## <a name="see-also"></a>Viz také:

- [Analýza překročení mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
