---
title: Uložit protokol zátěžového testu pro selhání testu
description: Naučte se, jak určit, zda má být protokol testu uložen v případě, že test selže v zátěžovém testu, změnou vlastnosti uložit protokol selhání testu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 2f4c81a364bdbe12bb3f780fe17c077ab04a615b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889431"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Postupy: určení, zda se chyby testu ukládají do protokolů testů pomocí Editor zátěžového testu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem** lze pomocí **Editor zátěžového testu** změnit vlastnosti zátěžového testu tak, aby vyhovovaly vašim požadavkům na testování a cílům. Viz [Návod: vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md). Můžete určit, zda má být protokol testu uložen v případě selhání testu v rámci zátěžového testu změnou vlastnosti **Uložit protokol selhání testu** .

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Určení, zda bude protokol testu při selhání testu ve scénáři uložen

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **nastavení spuštění** stromů zátěžového testu zvolte uzel nastavení spuštění, pro který chcete zadat maximální počet iterací testu pro.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti parametrů spuštění se zobrazí v okně **vlastnosti** .

4. V vlastnosti **Uložit protokol selhání testu** vyberte **hodnotu true** nebo **false** a určete, zda chcete uložit protokol testu v případě selhání testu ve scénáři.

     Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** .

     Data uložená v protokolu lze zobrazit pomocí tabulkového zobrazení v Analyzéru zátěžového testu. Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
