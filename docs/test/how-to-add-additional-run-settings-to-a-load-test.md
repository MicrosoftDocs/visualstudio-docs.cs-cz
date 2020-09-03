---
title: Přidání parametrů spuštění do zátěžového testu
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2f62b3e9797e411138590fc15b0fe872920d203
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288452"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Postupy: Přidání dalších parametrů spuštění do zátěžového testu

Parametry spuštění zátěžového testu určují celou řadu dalších nastavení. Patří mezi ně doba trvání testu, úroveň podrobností shromažďování výsledků a sady čítačů, které se shromažďují za běhu testu. Pro každý zátěžový test lze vytvořit a uložit několik parametrů spuštění a následně při spouštění testu zvolit jedno konkrétní nastavení. Počáteční nastavení spuštění je přidáno do zátěžového testu při vytváření zátěžového testu pomocí **nového Průvodce zátěžovým testem**.

K zátěžovému testu lze přidat více parametrů spuštění s různými nastaveními vlastností a spouštět tak zátěžový test za jiných podmínek. Lze například přidat nové nastavení testu a použít jinou vzorkovací frekvenci či zadat delší dobu běhu. V jednu chvíli lze používat pouze jeden parametr spuštění; parametr, který se má spustit, určíte tak, že jej nastavíte jako aktivní.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Přidání dalšího parametru spuštění

1. Otevřete zátěžový test.

2. Volitelné Rozbalte složku **parametry spuštění** .

3. Klikněte pravým tlačítkem na složku **parametry spuštění** a vyberte **Přidat nastavení spuštění**.

     Do složky **parametrů běhu** se přidá nové nastavení spuštění.

4. V nabídce **zobrazení** klikněte na příkaz **Vlastnosti okno**.

     Zobrazí se okno **vlastnosti** s vlastnostmi vybraného nastavení spuštění.

5. V okně **vlastnosti** pomocí textového pole u vlastnosti **název** udělte novému nastavení spuštění název, který popisuje záměr nastavení spuštění (například **nastavení spuštění: pět minut spuštění**).

6. Použijte okno **vlastnosti** ke změně parametrů běhu. Například můžete změnit dobu trvání běhu na **00:05:00** a spustit test po dobu pěti minut.

    > [!NOTE]
    > Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

     Aby byl přidaný parametr spuštění použit, nastavte jej jako aktivní. Další informace najdete v tématu [Postupy: výběr aktivního nastavení spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Viz také

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
