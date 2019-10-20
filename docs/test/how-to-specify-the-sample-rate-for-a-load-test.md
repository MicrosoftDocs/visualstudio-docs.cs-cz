---
title: 'Postupy: Určení vzorkovací frekvence v parametrech běhu zátěžového testu'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ea68c2a4c643a9fc06d9d831008a7ee8b684c2e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653370"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Postupy: určení vzorkovací frekvence pro nastavení běhu zátěžového testu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí **Editor zátěžového testu** změnit vlastnosti tak, aby splňovaly potřeby testování a cíle.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pomocí **Editor zátěžového testu**můžete upravit hodnotu vlastnosti **vzorkovací frekvence** nastavení běhu v okně **vlastnosti** . Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

Vyberte vhodnou hodnotu pro vlastnost **vzorkovací frekvence** pro nastavení spuštění zátěžového testu na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zkracuje vzorkovací frekvence omezení množství shromažďovaných dat. Další informace naleznete v tématu [Postupy: určení vzorkovací frekvence pro nastavení běhu zátěžového testu](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Tady jsou některé pokyny pro vzorkovací frekvence:

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\< 1 hodina|5 sekund|
|1-8 hodin|15 sekund|
|8-24 hodin|30 sekund|
|> 24 hodin|60 sekund|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Určení vzorkovací frekvence čítače výkonu v nastavení spuštění

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve stromové struktuře zátěžového testu ve složce **parametry spuštění** zvolte parametr spuštění, pro který chcete zadat vzorkovací frekvenci.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     V okně **vlastnosti** se zobrazí kategorie a vlastnosti nastavení běhu zatížení.

4. Do vlastnosti **vzorkovací frekvence** zadejte hodnotu času, která určuje četnost, s jakou bude zátěžový test shromažďovat data čítače výkonu.

5. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test s použitím nové hodnoty **vzorkovací frekvence** .

## <a name="see-also"></a>Viz také:

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)