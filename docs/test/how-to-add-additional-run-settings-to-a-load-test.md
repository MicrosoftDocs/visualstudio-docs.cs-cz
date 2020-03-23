---
title: Přidání nastavení spuštění do zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adcb50d2c6800c5ce64ab2b7cf16ce9d2a25aaaa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584501"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Postup: Přidání dalších nastavení spuštění do zátěžového testu

Parametry spuštění zátěžového testu určují celou řadu dalších nastavení. Patří mezi ně doba trvání testu, úroveň podrobností shromažďování výsledků a sady čítačů, které se shromažďují za běhu testu. Pro každý zátěžový test lze vytvořit a uložit několik parametrů spuštění a následně při spouštění testu zvolit jedno konkrétní nastavení. Počáteční nastavení spuštění je přidáno do zátěžového testu při vytváření zátěžového testu pomocí **Průvodce novým zátěžového testu**.

K zátěžovému testu lze přidat více parametrů spuštění s různými nastaveními vlastností a spouštět tak zátěžový test za jiných podmínek. Lze například přidat nové nastavení testu a použít jinou vzorkovací frekvenci či zadat delší dobu běhu. V jednu chvíli lze používat pouze jeden parametr spuštění; parametr, který se má spustit, určíte tak, že jej nastavíte jako aktivní.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Přidání dalšího parametru spuštění

1. Otevřete zátěžový test.

2. (Nepovinné) Rozbalte složku **Spustit nastavení.**

3. Klepněte pravým tlačítkem myši na složku **Spustit nastavení** a vyberte přidat **nastavení spuštění**.

     Do složky **Spustit nastavení** je přidáno nové nastavení spuštění.

4. V nabídce **View** zvolte **Properties Window**.

     Zobrazí se okno **Vlastnosti** s vlastnostmi vybraného nastavení spuštění.

5. V okně **Vlastnosti** použijte textové pole vlastnosti **Name** k tomu, aby nové nastavení spuštění bylo pojmenováním, které popisuje záměr nastavení spuštění (například **Spustit nastavení: Pět minut spuštění).**

6. Pomocí okna **Vlastnosti** změňte nastavení spuštění. Můžete například změnit dobu trvání spuštění na **00:05:00** a spusťte test po dobu pěti minut.

    > [!NOTE]
    > Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

     Aby byl přidaný parametr spuštění použit, nastavte jej jako aktivní. Další informace naleznete v [tématu Postup: Vyberte nastavení aktivního spuštění zátěžového testu](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
