---
title: Vyberte nastavení spuštění pro zátěžový test.
description: Zátěžový test může zahrnovat parametry spuštění, které jsou vlastnosti, které ovlivňují způsob spuštění zátěžového testu. Naučte se, jak vybrat aktivní nastavení spuštění.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87a67cb90ed48993e75dc248f23d10e982c64c43
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439859"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Postupy: výběr aktivního nastavení spuštění pro zátěžový test

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem** můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zátěžový test může obsahovat jedno nebo více *parametrů spuštění* , které jsou sadou vlastností ovlivňujících způsob, jakým běží zátěžový test. Nastavení spuštění jsou uspořádána podle kategorií v okně **vlastnosti** . Zátěžový test při svém spuštění používá parametry spuštění, které jsou aktuálně nastaveny jako aktivní.

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

Pokud zátěžový test obsahuje pouze jeden uzel nastavení spuštění ve složce **parametrů běhu** , je tento uzel vždy aktivním uzlem. Pokud zátěžový test obsahuje více uzlů parametrů spuštění, můžete vybrat, který má být použit při spuštění zátěžového testu. Viz [Postupy: Přidání dalších parametrů spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md).

V **Editor zátěžového testu** je nastavení aktivní spuštění identifikované příponou [Active].

## <a name="select-the-active-run-setting"></a>Vybrat aktivní nastavení běhu

1. Otevřete zátěžový test.

2. Rozbalte složku **parametry spuštění** .

3. Klikněte pravým tlačítkem myši na uzel nastavení spuštění, který chcete použít jako aktivní uzel, a pak zvolte **nastavit jako aktivní**.

     V **Edito zátěžového testu** se uzel ovlivněného spuštění aktualizuje s příponou [Active].

     Vybrané nastavení spuštění bude aktivní a zůstane aktivní, dokud nevyberete jiné nastavení spuštění.

> [!NOTE]
> Aktivní nastavení spuštění můžete přepsat nastavením proměnné prostředí s názvem `Test.UseRunSetting=<run setting name>` . To je užitečné při spuštění zátěžového testu z příkazového řádku nebo z dávkového souboru. To vám umožní zvolit různá nastavení spuštění bez nutnosti otevřít zátěžový test.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Zadejte nastavení běhu, které se má použít z příkazového řádku.

Výchozí parametry běhu v zátěžovém testu můžete přepsat nastavením proměnné prostředí z příkazového řádku:

**Nastavte test. UseRunSetting = PreProdEnvironment**

A ke spuštění testu:

**MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="see-also"></a>Viz také

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Postupy: Přidání dalších parametrů spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)
