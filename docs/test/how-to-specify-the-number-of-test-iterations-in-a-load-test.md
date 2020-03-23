---
title: Zadejte počet iterací testu v nastavení spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 446da348c1a947e6c59b8ad60d9bd0799d0d4322
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588938"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Postup: Určení počtu iterací testu v nastavení spuštění zátěžového testu

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování. Další informace naleznete [v tématu Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md).

Pomocí **Editoru zátěžového testu**můžete upravit vlastnost **Testovat iteraci** hodnoty nastavení spuštění v okně **Vlastnosti.** **Vlastnost Test Iterations** určuje počet iterací, které mají být spuštěny na všech testech výkonu webu a jednotkových testů ve všech scénářích v zátěžovém testu pomocí **editoru zátěžového testu**.

> [!NOTE]
> Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Určení počtu iterací testu v nastavení spuštění

1. Otevřete zátěžový test.

     Zobrazí se **editor zátěžového testu** a zobrazí strom zátěžového testu.

2. Ve stromu zátěžového testu zvolte ve složce **Spustit nastavení** spustit.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti,** chcete-li zobrazit kategorie a vlastnosti nastavení spuštění zatížení.

4. Nastavte vlastnost **Použít iteraci testů** na **hodnotu True**.

5. Ve vlastnosti **Test Iterace** zadejte číslo, které označuje počet iterací testu, které mají být spuštěny během zátěžového testu.

6. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **Test Iterace.**

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
