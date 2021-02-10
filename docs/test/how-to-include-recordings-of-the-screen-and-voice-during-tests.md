---
title: Záznam obrazovky a hlasu během testů
description: Naučte se konfigurovat adaptér diagnostických dat, který zaznamenává obrazovku a hlas uživatele, který spouští test v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 2ca477e25daa76e63e786698e7e2fa1e39c7f77f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961466"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Postupy: zahrnutí záznamů obrazovky a hlasu během testů pomocí nastavení testu

Z editoru konfigurace v aplikaci Visual Studio můžete nakonfigurovat adaptér diagnostických dat, který zaznamenává obrazovku a hlas uživatele, který spouští test. Tento adaptér diagnostických dat uloží obrazovku a záznam hlasu relace plochy během testu. Záznam je uložen s výsledkem testu nebo může být připojen k chybě. Jiní členové týmu mohou záznam použít k izolaci vad aplikace, které jsou obtížné reprodukovány.

> [!WARNING]
> Obrazovky a hlasové nahrávky nepodporují více konfigurací monitorování.

Záznam obrazovky a hlasu lze použít buď ručním, nebo automatizovaným testem. Například pokud spustíte programový test UI vzdáleně, může být vhodné zaznamenat plochu a zobrazit programový test UI při jeho spuštění. Další informace o tom, jak zaznamenat obrazovku a hlasový záznam vzdáleně, najdete v tématu [Postup: nastavení testovacího agenta pro spouštění testů, které pracují s plochou](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Konfigurace obrazovky a záznamu hlasu pro nastavení testu

1. Otevřete nastavení testu, které chcete konfigurovat pro záznam obrazovky a hlasu. Další informace najdete v tématu [shromáždění diagnostických dat při testování (Azure test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) nebo [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

2. V nastavení testu vyberte **roli** , kterou chcete použít pro záznam obrazovky a hlasu.

    > [!NOTE]
    > Pro manuální testy a automatizované testy by to byl počítač, který spouští testy.

3. Vyberte položku **záznam obrazovky a hlas** a pak zvolte možnost **Konfigurovat**.

     Zobrazí se dialogové okno **konfigurovat adaptér diagnostiky dat – obrazovka a hlasový záznam** .

     ![Konfigurace videa](../test/media/testsettingvideoconfiggdr.png)

4. Volitelné Vyberte **Povolit záznam hlasu** pro zachycení zvukového obsahu v záznamu.

5. Volitelné Zaškrtněte políčko vedle **Uložit záznam, pokud testovací případ projde** , a určete ukládání obrazovky a hlasové nahrávky pro neúspěšné i úspěšné testy.

    > [!WARNING]
    > Pokud vyberete možnost **Uložit záznam, pokud testovací případ projde**, záznam je uložen s výsledky testu, který využívá prostor úložiště na serveru. K vyčištění těchto příloh můžete použít nástroj pro **čištění příloh testu** .

6. V části **kvalita záznamu obrazovky** nakonfigurujte následující možnosti rozevíracího seznamu:

    1. **Snímková frekvence:** Zadejte, kolik snímků za sekundu chcete použít na obrazovce a v záznamu hlasu. Výchozí hodnota je 4 snímky za sekundu. Je možné zadat hodnoty mezi 2 a 20.

    2. **Přenosová rychlost:** Zadejte počet kilobajtů za sekundu, které se mají použít na obrazovce a v záznamu hlasu. Výchozí hodnota je 512. Je možné zadat hodnoty mezi 512 a 10 000.

    3. **Kvalita (1-100):** Můžete určit kvalitu záznamu obrazovky a hlasu tak, že vyberete rozsah mezi 1 a 100. Výchozí hodnota je 50 (střední-rozsah).

7. Vyberte **OK**. Nastavení kolektoru trasování diagnostiky jsou nyní konfigurována a uložena pro nastavení testu.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Chcete-li obnovit konfiguraci pro tento adaptér diagnostických dat, vyberte možnost **Obnovit výchozí konfiguraci** pro aplikaci Visual Studio a **nastavte výchozí hodnotu** pro Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Chcete-li obnovit konfiguraci pro tento adaptér diagnostických dat, vyberte možnost **obnovit na výchozí konfiguraci** v aplikaci Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Viz také

- [Shromažďovat diagnostická data při testování (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Shromažďovat diagnostická data v ručních testech (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Spustit Manuální testy (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)