---
title: Nastavení protokolování zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c0a9967f1248c6dc23c5d70be35788ad9e05eb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566303"
---
# <a name="modify-load-test-logging-settings"></a>Změna nastavení protokolování zátěžového testu

Výsledek dokončeného zátěžového testu obsahuje vzorky čítače výkonu a informace o chybách pravidelně shromažďované z testovaných počítačů do protokolu. Velký počet vzorků čítače výkonu mohou být shromažďovány v průběhu spuštění zátěžového testu. Množství shromážděných dat o výkonu závisí na délce běhu, intervalu vzorkování, počtu testovaných počítačů a počtu shromažďovaných čítačů. U velkých zátěžových testů může množství shromážděných dat o výkonu snadno dosáhnout několika GB, proto zvažte úpravu četnosti ukládání dat do protokolu. Viz [Testovací řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Testovací řadič* zavěsí všechna shromážděná ukázková data zátěžového testu do protokolu databáze, zatímco je test spuštěn. Další data, jako jsou podrobnosti časování a podrobnosti o chybě, se načtou do databáze po dokončení testu.

|Úkol|Přidružená témata|
|-|-----------------------|
|**Pokud se podaří, uložte protokoly, pokud se podaří zátěžový test:** Můžete určit, zda chcete uložit protokol testu vždy, když se nezdaří zátěžový test.|-   [Postup: Určete, zda jsou uloženy chyby testu pro testovací protokoly](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Nastavte maximální velikost souboru pro soubor protokolu:** Můžete upravit konfigurační soubor XML, který je přidružen ke službě testovacího řadiče, a určit tak maximální velikost souboru, který chcete použít pro soubor protokolu.|Upravte `<add key="LogSizeLimitInMegs" value="20"/>` v konfiguračním souboru XML *QTCcontroller.exe.config.*|

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
