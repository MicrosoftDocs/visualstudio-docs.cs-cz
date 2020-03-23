---
title: Záznam obrazovky a hlasu během testů
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94d8fdc2765b3a073ca481d09bc38dfbc9b38f2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589016"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Postup: Zahrnout nahrávky obrazovky a hlasu během testů pomocí nastavení testu

Z konfiguračního editoru v sadě Visual Studio můžete nakonfigurovat adaptér diagnostických dat, který zaznamenává obrazovku a hlas uživatele, který test spouštěl. Tento adaptér diagnostických dat ukládá během testu obrazovku a hlasový záznam relace plochy. Záznam je uložen s výsledkem testu nebo může být připojen k chybě. Ostatní členové týmu můžete použít záznam izolovat vady aplikace, které je obtížné reprodukovat.

> [!WARNING]
> Obrazovky a hlasové záznamy nepodporují více konfigurací monitoru.

Obrazovku a hlasový záznamník lze použít s manuálními nebo automatizovanými testy. Například pokud spustíte kódovaný test uživatelského prostředí vzdáleně, můžete chtít zaznamenat plochu, aby se viděl kódovaný test uživatelského prostředí při jeho spuštění. Další informace o vzdáleném zachycení záznamu obrazovky a hlasu naleznete v tématu [Postup: Nastavení testovacího agenta pro spuštění testů, které interagují s plochou](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Konfigurace nahrávání obrazovky a hlasu pro nastavení testu

1. Otevřete nastavení testu, které chcete nakonfigurovat pro záznam obrazovky a hlasu. Další informace najdete [v tématu Shromažďování diagnostických dat při testování (Plány testů Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts) nebo [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

2. V nastavení testu vyberte **roli,** která se má použít k záznamu obrazovky a hlasu.

    > [!NOTE]
    > Pro ruční testy a automatizované testy by to byl stroj, který spustí testy.

3. Vyberte **Screen a Voice Recorder** a pak zvolte **Konfigurovat**.

     Zobrazí se dialogové okno **Konfigurovat adaptér diagnostických dat – obrazovka a hlasový záznamník.**

     ![Konfigurace videa](../test/media/testsettingvideoconfiggdr.png)

4. (Nepovinné) Vyberte **Povolit záznam hlasu,** chcete-li zachytit zvukový obsah v záznamu.

5. (Nepovinné) Zaškrtněte políčko vedle **možnosti Uložit záznam, pokud testovací případ projde,** chcete-li určit uložení obrazovky a hlasových nahrávek pro neúspěšné i prošlé testy.

    > [!WARNING]
    > Pokud vyberete **uložit záznam, pokud testovací případ projde**, záznam je uložen s výsledky testu, který používá úložný prostor na serveru. K vyčištění těchto příloh můžete použít nástroj **Test Attachment Cleaner.**

6. V části **Kvalita záznamu obrazovky**nakonfigurujte následující možnosti rozevíracího seznamu:

    1. **Kmitočet snímků:** Určete, kolik snímků za sekundu chcete použít na obrazovce a hlasový záznam. Výchozí hodnota je 4 snímky za sekundu. Lze zadat hodnoty mezi 2 a 20.

    2. **Přenosová rychlost:** Určete, kolik kilobajtů za sekundu se má použít na obrazovce a hlasový záznam. Výchozí hodnota je 512. Lze zadat hodnoty mezi 512 a 10 000.

    3. **Kvalita (1-100):** Kvalitu obrazovky a záznamu hlasu můžete určit výběrem rozsahu mezi 1 a 100. Výchozí hodnota je 50 (střední rozsah).

7. Vyberte **OK**. Nastavení kolektoru diagnostických trasování jsou nyní nakonfigurována a uložena pro nastavení testu.

    > [!TIP]
    > Chcete-li obnovit konfiguraci tohoto adaptéru diagnostických dat, zvolte **Obnovit na výchozí konfiguraci** pro sadu Visual Studio a **Obnovit výchozí** pro Správce testů společnosti Microsoft.

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických dat během testování (plány testů Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Shromažďování diagnostických dat v ručních testech (plány testů Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Spuštění ručních testů (plány testů Azure)](/azure/devops/test/run-manual-tests?view=vsts)
