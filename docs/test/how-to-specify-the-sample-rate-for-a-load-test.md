---
title: 'Postupy: Určení vzorkovací frekvence v parametrech běhu zátěžového testu'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63b6b9479347b076b7bd9e350e80e4bfa2a36d69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594822"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Postup: Určení vzorkovací frekvence pro nastavení spuštění zátěžového testu

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti tak, aby vyhovovaly vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pomocí **Editoru zátěžového testu**můžete upravit hodnotu vlastnosti **Ukázkové rychlosti** nastavení spuštění v okně **Vlastnosti.** Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

Zvolte vhodnou hodnotu pro vlastnost **Vzorkovací frekvence** pro nastavení spuštění zátěžového testu na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zvyšuje vzorkovací frekvence množství dat, která shromažďujete. Další informace naleznete v [tématu Postup: Určení vzorkovací frekvence pro nastavení spuštění zátěžového testu](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Zde jsou některé pokyny pro vzorkovací frekvence:

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\<1 hodina|5 sekund|
|1 - 8 hodin|15 sekund|
|8 - 24 hodin|30 sekund|
|> 24 hodin|60 sekund|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Určení vzorkovací frekvence čítače čítače výkonu v nastavení spuštění

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve stromu zátěžového testu zvolte ve složce **Spustit nastavení** spustit nastavení, pro které chcete zadat vzorkovací frekvenci.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti nastavení spuštění zatížení se zobrazí v okně **Vlastnosti.**

4. Do vlastnosti **Vzorkovací frekvence** zadejte hodnotu času, která označuje frekvenci, při které bude zátěžový test shromažďovat data čítače výkonu.

5. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové **hodnoty vzorkovací frekvence.**

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
