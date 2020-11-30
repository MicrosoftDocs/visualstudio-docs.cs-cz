---
title: Nastavení protokolování zátěžového testu
description: Naučte se, jak upravit nastavení protokolování zátěžového testu, abyste mohli řídit množství shromážděných dat o výkonu, což může vést k velmi rozsáhlým souborům výsledků.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 464429ef516d3f4cd6dadd013f274139eb106a57
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329195"
---
# <a name="modify-load-test-logging-settings"></a>Změnit nastavení protokolování zátěžového testu

Výsledek dokončeného zátěžového testu obsahuje vzorky čítače výkonu a informace o chybách pravidelně shromažďované z testovaných počítačů do protokolu. V průběhu běhu zátěžového testu lze shromáždit velký počet ukázek čítače výkonu. Množství shromážděných dat o výkonu závisí na délce běhu, intervalu vzorkování, počtu testovaných počítačů a počtu shromažďovaných čítačů. U velkých zátěžových testů může množství shromážděných dat o výkonu snadno dosáhnout několika GB, proto zvažte úpravu četnosti ukládání dat do protokolu. Viz [testovací kontroléry a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Testovací kontrolér* zařadí všechna shromážděná ukázková data zátěžového testu do protokolu databáze v době, kdy je spuštěn test. Další data, jako jsou podrobnosti časování a podrobnosti chyby, jsou načtena do databáze po dokončení testu.

|Úkol|Přidružená témata|
|-|-----------------------|
|**Ukládat protokoly v případě neúspěchu zátěžového testu:** Můžete určit, zda chcete uložit protokol testu pokaždé, když dojde k chybě zátěžového testu.|-   [Postupy: určení, zda se chyby testu ukládají do protokolů testu](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Nastavte maximální velikost souboru protokolu:** Můžete upravit konfigurační soubor XML, který je přidružený ke službě testovacího kontroléru, a určit tak maximální velikost souboru, kterou chcete použít pro soubor protokolu.|Upravte `<add key="LogSizeLimitInMegs" value="20"/>` v konfiguračním souboru *QTCcontroller.exe.config* XML.|

## <a name="see-also"></a>Viz také

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
