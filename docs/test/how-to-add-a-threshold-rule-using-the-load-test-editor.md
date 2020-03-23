---
title: Přidání pravidla prahové hodnoty pro zátěžové testování
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591629"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Postup: Přidání pravidla prahové hodnoty pomocí editoru zátěžového testu

Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Chcete-li přidat mezní pravidlo:

1. Otevřete zátěžový test.

2. V Editoru zátěžového testu rozbalte uzel **Sady čítačů.**

3. Rozbalte jednu z **kategorií čítačů** v jedné ze sad čítačů. Můžete například vybrat **Možnost LoadTest:Scénář**. Rozbalte uzel.

4. Klepněte pravým tlačítkem myši na jeden z čítačů, například **Načíst uživatele**, v části **LoadTest:Scenario**. Vyberte **přidat pravidlo prahové hodnoty**.

     Zobrazí se dialogové okno **Přidat pravidlo prahové hodnoty.**

5. Můžete si vybrat ze dvou typů pravidel: **Porovnat konstantu** a **Porovnat čítač**. Vyberte požadovaný typ a nastavte hodnoty.

    > [!NOTE]
    > Nastavte **Alert If Over** vlastnost **True** označuje, že překročení prahové hodnoty je problém, nebo **False** označuje, že spadají pod prahovou hodnotu je problém.

## <a name="see-also"></a>Viz také

- [Analyzovat porušení pravidel prahových hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
