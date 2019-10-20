---
title: Přidat prahové pravidlo pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecec4826966205d849c07169da954198d687696
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644431"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Postupy: Přidání prahového pravidla pomocí editoru zátěžových testů

Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Chcete-li přidat mezní pravidlo:

1. Otevřete zátěžový test.

2. V Editor zátěžového testu rozbalte uzel **sady čítačů** .

3. Rozbalte jednu z **kategorií čítače** v jedné ze sad čítačů. Můžete například vybrat **LoadTest: Scenario**. Rozbalte uzel.

4. Klikněte pravým tlačítkem na jeden z čítačů, například **uživatelské zatížení**, v části **LoadTest: Scenario**. Vyberte **Přidat pravidlo prahové hodnoty**.

     Zobrazí se dialogové okno **Přidat pravidlo prahové hodnoty** .

5. Můžete si vybrat ze dvou typů pravidel: **porovnání čítače konstanty** a **porovnání**. Vyberte požadovaný typ a nastavte hodnoty.

    > [!NOTE]
    > Nastavte **výstrahu, pokud** má vlastnost over na **hodnotu true** , aby označovala, že překročení prahové hodnoty je problém, nebo na **hodnotu false** , aby označovala, že se jedná o problém s prahovou hodnotou.

## <a name="see-also"></a>Viz také:

- [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
