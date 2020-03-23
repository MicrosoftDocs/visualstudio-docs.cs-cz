---
title: Výběr nastavení spuštění pro zátěžový test
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91ac811c1f55fdb9a662db679ebd2d038ecdd5dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588977"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Postup: Vyberte nastavení aktivního spuštění pro zátěžový test

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zátěžový test může obsahovat jedno nebo více *nastavení spuštění,* které jsou sadou vlastností, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **Vlastnosti.** Zátěžový test při svém spuštění používá parametry spuštění, které jsou aktuálně nastaveny jako aktivní.

> [!NOTE]
> Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

Pokud zátěžový test obsahuje pouze jeden uzel nastavení spuštění ve složce **Spustit nastavení,** tento uzel je vždy aktivní uzel. Pokud zátěžový test obsahuje více uzlů nastavení spuštění, můžete vybrat ten, který chcete použít při spuštění zátěžového testu. Viz [Postup: Přidání dalších nastavení spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md).

V **Editoru zátěžového testu**je nastavení aktivního spuštění identifikováno příponou "[Active]..

## <a name="select-the-active-run-setting"></a>Výběr nastavení aktivního spuštění

1. Otevřete zátěžový test.

2. Rozbalte složku **Spustit nastavení.**

3. Klepněte pravým tlačítkem myši na uzel nastavení spuštění, který má být aktivním uzlovým uzlovým, a pak zvolte **Nastavit jako aktivní**.

     V **zátěžovém testu Edito**r je ovlivněný uzel nastavení spuštění aktualizován příponou "[Active]."

     Vybrané nastavení spuštění se aktivuje a zůstane aktivní, dokud nevyberete jiné nastavení spuštění, aby bylo aktivní.

> [!NOTE]
> Nastavení aktivního spuštění můžete přepsat nastavením `Test.UseRunSetting=<run setting name>`proměnné prostředí s názvem . To je užitečné při spuštění zátěžového testu z příkazového řádku nebo z dávkového souboru. To umožňuje zvolit různé nastavení spuštění bez otevření zátěžového testu.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Určení nastavení spuštění, které se má použít z příkazového řádku

Výchozí nastavení spuštění v zátěžovém testu můžete přepsat nastavením proměnné prostředí z příkazového řádku:

**Nastavit test.UseRunSetting=PreProdEnvironment**

A spustit test:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Postup: Přidání dalších nastavení spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)
