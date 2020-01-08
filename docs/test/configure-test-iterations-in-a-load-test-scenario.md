---
title: Konfigurace iterací testů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e95ca27ace50c7b28d1ffb1d3fc02589daddee2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590979"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurace iterací testů ve scénáři zátěžového testu

Konfigurace nastavení iterace testu, upravte do scénáře zátěžového testu pomocí editoru zátěžových testů a **vlastnosti** okna. Ve výchozím nastavení se bez určení maximálního počtu testovacích iterací nastavení scénáře zátěžového testu. Máte možnost konfigurace maximální počet iterací ve scénáři a délkou prodlevy mezi nimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Zadejte maximální počet iterací scénáře

Můžete určit maximální počet případů, kdy chcete, aby ke spuštění testů pro scénář pomocí editoru zátěžových testů, chcete-li změnit **maximální testovací iterace** vlastnost **vlastnosti** okna.

**Maximální testovací iterace** vlastnost určuje maximální počet iterací testu pro spuštění scénáře. Stejně jako u **testovací iterace** parametrů běhu a vlastnost v zátěžovém testu, což není maximální počet přes všechny uživatele na všech agentech, za nastavení hlavního názvu uživatele.

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Kombinace sekvenčního testu jedné iterace je jednom průchodu přes všechny testy v kombinaci. Pro všechny ostatní mix testů každé spuštění testu se počítá jako iterace. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Pokud zátěžový test je založené na době trvání zátěžového testu a dobu trvání vyprší před dokončením počet iterací, test bude stále zastavit. Pokud test je založená na iterace a iterace testů jsou splnit, abyste mohli iterací scénáře, test se zastaví. Doba trvání se konfiguruje pomocí **doba běhu** vlastnost **vlastnosti** okno, které jsou přidružené k parametrům spuštění zátěžového testu.

Počet iterací scénáře při splnění, tento scénář se zastaví, ale jiné aktivní scénáře budou nadále spuštěné.

> [!NOTE]
> Související vlastností je **jedinečné** vlastností webového testu zdroje dat, která prochází postupně data, řádek po řádku, ale pouze jeden čas pro každý záznam. Další informace najdete v tématu [přidat zdroj dat do testu výkonnosti webu](../test/add-a-data-source-to-a-web-performance-test.md).

**Maximální testovací iterace** vlastnost je užitečná pro celou řadu situací. Testery zatížení raději chování iterační testování, zatímco jiné zatížení testery raději proveďte založené na době trvání test.

![Určení iterací testů ve scénáři](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Chcete-li určit maximální počet iterací

1. Otevřete zátěžový test.

2. Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

3. V zátěžového testu stromů **scénáře** složky, vyberte uzel scénáře, pro kterou chcete určit maximální počet iterací testu.

4. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v **vlastnosti** okna.

5. V textovém poli pro **maximální testovací iterace** vlastnost, typ a hodnotu, která určuje maximální počet testů ke spuštění pro scénář při spuštění zátěžového testu.

    > [!NOTE]
    > Hodnota 0 pro použití **maximální testovací iterace** vlastnost určuje žádné maximální počet iterací.

6. Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **maximální testovací iterace** hodnotu.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Zadat čas přemýšlení mezi testovacími iteracemi pro scénář

**Myslíte, že doba mezi cykly testu** vlastnost použití nastavena **vlastnosti** okno při úpravě vlastnosti scénáře zátěžového testu v editoru zátěžového testu.

**Myslíte, že doba mezi cykly testu** vlastnost se používá k určení množství sekund se má čekat před zahájením iteraci testu.

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v části [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>K určení doby uvažování mezi iteracemi testu

1. Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V zátěžového testu stromů **scénáře** složky, zvolte uzel scénář, který chcete zadat čas přemýšlení pro.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Tento scénář kategorie a vlastnosti jsou zobrazeny v **vlastnosti** okna.

4. V hodnotě **myslíte, že doba mezi cykly testu** vlastnost, zadejte číslo představující počet sekund se má čekat před spuštěním další iterace testu.

5. Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **myslíte, že doba mezi cykly testu** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovací kontrolery pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úpravy dob uvažování pro simulaci prodlev při zásahem ze strany webové stránky](../test/edit-think-times-in-load-test-scenarios.md)
