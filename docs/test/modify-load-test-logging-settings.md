---
title: Nastavení protokolování zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 64e65a08910757d564e1fca0d3280770a1a60af9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646656"
---
# <a name="modify-load-test-logging-settings"></a>Změnit nastavení protokolování zátěžového testu

Výsledek dokončeného zátěžového testu obsahuje vzorky čítače výkonu a informace o chybách pravidelně shromažďované z testovaných počítačů do protokolu. V průběhu běhu zátěžového testu lze shromáždit velký počet ukázek čítače výkonu. Množství shromážděných dat o výkonu závisí na délce běhu, intervalu vzorkování, počtu testovaných počítačů a počtu shromažďovaných čítačů. U velkých zátěžových testů může množství shromážděných dat o výkonu snadno dosáhnout několika GB, proto zvažte úpravu četnosti ukládání dat do protokolu. Viz [testovací kontroléry a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Testovací kontrolér* zařadí všechna shromážděná ukázková data zátěžového testu do protokolu databáze v době, kdy je spuštěn test. Další data, jako jsou podrobnosti časování a podrobnosti chyby, jsou načtena do databáze po dokončení testu.

|Úloha|Přidružená témata|
|-|-----------------------|
|**Ukládat protokoly v případě neúspěchu zátěžového testu:** Můžete určit, zda chcete uložit protokol testu pokaždé, když dojde k chybě zátěžového testu.|-   [Postupy: určení, zda se chyby testu ukládají do protokolů testu](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Nastavte maximální velikost souboru protokolu:** Můžete upravit konfigurační soubor XML, který je přidružený ke službě testovacího kontroléru, a určit tak maximální velikost souboru, kterou chcete použít pro soubor protokolu.|V konfiguračním souboru *konfigurační soubor QTCcontroller. exe. config* XML upravte `<add key="LogSizeLimitInMegs" value="20"/>`.|

## <a name="see-also"></a>Viz také:

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)