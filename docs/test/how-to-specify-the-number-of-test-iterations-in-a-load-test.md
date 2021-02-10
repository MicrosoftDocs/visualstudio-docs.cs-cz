---
title: Zadejte počet iterací v nastavení běhu zátěžového testu.
description: Naučte se, jak zadat počet iterací, které se mají spustit na všech testech webového výkonu a jednotek ve všech scénářích zátěžového testu pomocí Editor zátěžového testu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a257b5800166e840194a28cba0ca99849b05f579
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936194"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Postupy: určení počtu testovacích iterací v nastavení spuštění zátěžového testu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem** můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům. Další informace naleznete v tématu [Návod: vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md).

Pomocí **Editor zátěžového testu** můžete upravit vlastnost **iterace testu** hodnoty parametrů běhu v okně **vlastnosti** . Vlastnost **iterace testu** určuje počet iterací, které se mají spustit na všech testech webového výkonu a jednotek ve všech scénářích zátěžového testu pomocí **Editor zátěžového testu**.

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Určení počtu testovacích iterací v nastavení spuštění

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** a zobrazí se strom zátěžového testu.

2. Ve stromové struktuře zátěžového testu ve složce **parametry spuštění** vyberte nastavení spuštění.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti** a zobrazte kategorie a vlastnosti nastavení spuštění zatížení.

4. Nastavte vlastnost **použít iterace testu** na **hodnotu true**.

5. Do vlastnosti **iterace testu** zadejte číslo, které označuje počet iterací testu, které mají být spuštěny během zátěžového testu.

6. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test s použitím nové hodnoty **iterace testu** .

## <a name="see-also"></a>Viz také

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
