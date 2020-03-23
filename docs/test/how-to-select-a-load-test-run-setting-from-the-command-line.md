---
title: Nastavení spuštění zátěžového testu z příkazového řádku
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 760cf18062e607e9f9039c6cc5f4adf409134cb5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588990"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Postup: Vyberte nastavení spuštění zátěžového testu, které se má použít z příkazového řádku.

Zátěžový test může zahrnovat *nastavení spuštění*, což jsou vlastnosti, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **Vlastnosti.** Zátěžový test při svém spuštění používá parametry spuštění, které jsou aktuálně nastaveny jako aktivní.

Pokud zátěžový test obsahuje pouze jeden parametr spuštění, jedná se vždy o aktivní uzel. Pokud zátěžový test obsahuje více uzlů nastavení spuštění, můžete vybrat ten, který chcete použít při spuštění zátěžového testu z příkazového řádku. Viz [Postup: Přidání dalších nastavení spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Změna nastavení spuštění z příkazového řádku

1. Chcete-li použít jiné nastavení spuštění z příkazového řádku, abyste využili výhod strategie parametrů kontextu, použijte následující příkaz:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Spusťte zátěžový test pomocí nástroje mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Postup: Přidání dalších nastavení spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Postup: Vyberte nastavení aktivního spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
