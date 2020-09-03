---
title: Ladění nainstalovaného balíčku aplikace pro UWP | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: how-to
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350729"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Ladění nainstalovaného balíčku aplikace pro UWP v aplikaci Visual Studio

Visual Studio může ladit nainstalované balíčky aplikací Univerzální platforma Windows (UWP) na počítačích s Windows 10 a zařízeních Xbox, HoloLens a IoT.

>[!NOTE]
>Ladění sady Visual Studio pro nainstalované aplikace UWP není na telefonech podporováno.

Další informace o ladění aplikací pro UWP najdete v blogovém příspěvku o [ladění nainstalovaných balíčků aplikací](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) a [vytváření univerzálních aplikací pro Windows (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Ladění nainstalované aplikace UWP na místním počítači

1. V aplikaci Visual Studio vyberte **ladit**  >  **Další cíle ladění**  >  **ladění nainstalovaného balíčku aplikace**.

1. V dialogovém okně **ladění nainstalovaného balíčku aplikace** v části **Typ připojení**vyberte **místní počítač**.

1. V části **nainstalované balíčky aplikací**vyberte aplikaci, kterou chcete ladit, nebo zadejte její název do vyhledávacího pole. Nespuštěné balíčky aplikací se zobrazují pod **nespuštěným**a běžící aplikace jsou **spuštěné**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. V případě potřeby změňte typ kódu v části **ladit tento typ kódu**a vyberte další možnosti.
   - Vyberte možnost **nespouštět, ale ladit můj kód při** spuštění ladění při spuštění aplikace. Spuštění ladění, když se aplikace spustí, je účinný způsob, jak ladit cesty ovládacích prvků z [různých metod spuštění](/windows/uwp/xbox-apps/automate-launching-uwp-apps), jako je aktivace protokolu s vlastními parametry.

1. Vyberte **Spustit**, nebo pokud je aplikace spuštěná, vyberte **připojit**.

> [!NOTE]
> Můžete se také připojit k jakémukoli běžícímu UWP nebo jinému procesu aplikace výběrem možnosti **ladit**  >  **připojit k procesu** v aplikaci Visual Studio. Nepotřebujete, aby byl původní projekt sady Visual Studio připojen ke spuštěnému procesu, ale načítání symbolů aplikace pomůže významně při ladění procesu, pro který nemáte původní kód. Viz téma [Určení symbolů a zdrojových souborů v ladicím programu](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Ladění nainstalované aplikace UWP na vzdáleném počítači nebo zařízení

Když Visual Studio poprvé ladit nainstalovanou aplikaci UWP na zařízení s Windows 10 nebo na vzdáleném počítači s aktualizací Windows 10, nainstaluje na cílovém zařízení nástroje pro vzdálené ladění.

1. [Povolte vývojářský režim](/windows/uwp/get-started/enable-your-device-for-development) na počítači se systémem Visual Studio a na vzdáleném zařízení nebo počítači.

1. Pokud se připojujete ke vzdálenému počítači, na kterém je spuštěný systém Windows 10 s aktualizací předběžného autora, [ručně nainstalujte a spusťte vzdálený ladicí program](../debugger/remote-debugging.md) na vzdáleném počítači.

1. V počítači se systémem Visual Studio vyberte **ladit**  >  **Další cíle ladění**  >  **ladění nainstalovaného balíčku aplikace**.

1. V dialogovém okně **ladění nainstalovaného balíčku aplikace** v části **Typ připojení**vyberte možnost **vzdálený počítač** nebo **zařízení**.

   Pokud vyberete **zařízení**, musí být počítač fyzicky připojený k zařízení s Windows 10.

   Pokud se adresa počítače na vzdáleném počítači nezobrazí vedle pole **adresa**, vyberte **změnit**.

   1. V dialogovém okně **vzdálené připojení** do pole **adresa**zadejte název nebo IP adresu počítače, ke kterému se chcete připojit.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Pokud se ladicí program nemůže připojit ke vzdálenému počítači pomocí názvu počítače, použijte místo něj IP adresu. Použijte IP adresu pro zařízení Xbox, HoloLens nebo IoT.
   1. Vyberte možnost ověřování vedle možnosti **režim ověřování**.

      U většiny aplikací ponechte výchozí hodnotu **univerzální (nešifrovaný protokol)**.
   1. Vyberte **Vybrat**.

1. V části **nainstalované balíčky aplikací**vyberte aplikaci, kterou chcete ladit, nebo zadejte její název do vyhledávacího pole. Nespuštěné balíčky aplikací se zobrazují pod **nespuštěným**a běžící aplikace jsou **spuštěné**.

1. V případě potřeby změňte typ kódu v části **ladit tento typ kódu**a vyberte další možnosti.
   - Vyberte možnost **nespouštět, ale ladit můj kód při** spuštění ladění při spuštění aplikace. Spuštění ladění, když se aplikace spustí, je účinný způsob, jak ladit cesty ovládacích prvků z [různých metod spuštění](/windows/uwp/xbox-apps/automate-launching-uwp-apps), jako je aktivace protokolu s vlastními parametry.

1. Vyberte **Spustit**, nebo pokud je aplikace spuštěná, vyberte **připojit**.

Když poprvé spustíte ladění nainstalovaného balíčku aplikace na připojené zařízení Xbox, HoloLens nebo IoT, Visual Studio nainstaluje správnou verzi vzdáleného ladicího programu pro cílové zařízení. Instalace vzdáleného ladicího programu může nějakou dobu trvat a zpráva o **spuštění vzdáleného ladicího programu** se zobrazí, když se děje.

>[!NOTE]
>V současné době zařízení Xbox nebo HoloLens restartuje aplikaci pomocí připojeného ladicího programu, pokud už je spuštěný.

Další informace o vzdáleném nasazení aplikací pro UWP najdete v tématu [nasazení a ladění aplikací pro UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) a [ladění aplikací pro UWP na vzdálených počítačích](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)