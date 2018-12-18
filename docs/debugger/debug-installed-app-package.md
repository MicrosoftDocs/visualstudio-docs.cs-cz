---
title: Ladit nainstalovaný balíček aplikace UPW | Dokumentace Microsoftu
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 331fd642001f1e6217736185d4b3bbbd7f56923e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784413"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Ladit nainstalovaný balíček aplikace UWP v sadě Visual Studio

Visual Studio dokáže ladit nainstalované balíčky aplikací univerzální platformy Windows (UPW) na počítače s Windows 10 a Xbox, HoloLens a IoT zařízení. 

>[!NOTE]
>Visual Studio, ladění pro nainstalované aplikace UPW se nepodporuje na telefonech.
   
Další informace o ladění aplikací pro UWP, najdete v blogových příspěvků na [ladění nainstalované balíčky aplikací](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) a [vytváření univerzálních aplikací pro Windows (UPW)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Ladit aplikaci UPW nainstalované na místním počítači

1. V sadě Visual Studio, vyberte **ladění** > **jiné cíle ladění** > **ladit nainstalovaný balíček aplikace**.
   
1. V **ladit nainstalovaný balíček aplikace** dialogového okna, v části **typ připojení**vyberte **místního počítače**.
   
1. V části **nainstalované balíčky aplikací**, vyberte aplikaci, kterou chcete ladit, nebo zadejte jeho název do pole Hledat. Nainstalované aplikace běžící mimo balíčky zobrazí v části **neběží**, a jsou spuštěné aplikace v rámci **systémem**. 
   
   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")
   
1. V případě potřeby změňte typ kódu v rámci **ladit tento typ kódu**a vyberte další možnosti. 
   - Vyberte **nespouštět, ale ladit můj kód při spuštění** pro spuštění ladění při spuštění aplikace. Spouští se ladění při spuštění aplikace je účinný způsob, jak ladit ovládací prvek cesty z [různých spuštění metody](/windows/uwp/xbox-apps/automate-launching-uwp-apps), jako je protokol aktivace pomocí vlastních parametrů.
   
1. Vyberte **Start**, nebo pokud aplikace běží, vyberte **připojit**.

> [!NOTE]
> Můžete připojit také všechny spuštěné UPW nebo jiný proces aplikace tak, že vyberete **ladění** > **připojit k procesu** v sadě Visual Studio. Není nutné se připojit ke spuštěnému procesu původní projekt sady Visual Studio, ale načítají se symboly aplikace pomůže výrazně při ladění procesu, který není nutné původní kód. Zobrazit [určit symboly a zdrojové soubory v ladicím programu](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
## <a name="remote"></a> Ladit aplikaci UPW nainstalovaný na vzdáleném počítači nebo zařízení

Prvním spuštění sady Visual Studio ladí aplikaci UPW nainstalovanou na zařízení s Windows 10 nebo vzdáleného post Tvůrce příslušného počítače aktualizace Windows 10, nainstaluje nástroje vzdálené ladění na cílovém zařízení. 

1. [Povolení režimu pro vývojáře](/windows/uwp/get-started/enable-your-device-for-development) na počítači aplikace Visual Studio a vzdálené zařízení nebo počítače.
   
1. Pokud se chcete připojit ke vzdálenému počítači se systémem Windows 10 Update pre tvůrce, [ručně nainstalovat a spustit vzdálený ladicí program](../debugger/remote-debugging.md) na vzdáleném počítači.
   
1. Na počítači, Visual Studio, vyberte **ladění** > **jiné cíle ladění** > **ladit nainstalovaný balíček aplikace**.
   
1. V **ladit nainstalovaný balíček aplikace** dialogového okna, v části **typ připojení**vyberte **vzdálený počítač** nebo **zařízení**.
   
   Pokud vyberete **zařízení**, počítač musí být fyzicky připojen k zařízení s Windows 10.
   
   Pro vzdálený počítač, pokud se nezobrazí adresu počítače vedle **adresu**vyberte **změnu**. 
      
   1. V **připojení ke vzdálené** dialogového okna do pole **adresu**, zadejte název nebo IP adresu počítače, které se chcete připojit.
      
      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")
      
      Pokud ladicí program nemůže připojit ke vzdálenému počítači pomocí názvu počítače, použijte IP adresu. Použijte IP adresu pro Xbox, HoloLens a IoT zařízení.
   1. Vyberte možnost ověřování vedle **režim ověřování**.
      
      Pro většinu aplikací, ponechte výchozí hodnotu, **univerzální (nešifrovaný protokol)**.
   1. Vyberte **vyberte**. 

1. V části **nainstalované balíčky aplikací**, vyberte aplikaci, kterou chcete ladit, nebo zadejte jeho název do pole Hledat. Nainstalované aplikace běžící mimo balíčky zobrazí v části **neběží**, a jsou spuštěné aplikace v rámci **systémem**. 
   
1. V případě potřeby změňte typ kódu v rámci **ladit tento typ kódu**a vyberte další možnosti. 
   - Vyberte **nespouštět, ale ladit můj kód při spuštění** pro spuštění ladění při spuštění aplikace. Spouští se ladění při spuštění aplikace je účinný způsob, jak ladit ovládací prvek cesty z [různých spuštění metody](/windows/uwp/xbox-apps/automate-launching-uwp-apps), jako je protokol aktivace pomocí vlastních parametrů.
   
1. Vyberte **Start**, nebo pokud aplikace běží, vyberte **připojit**.

Při zahájení ladění balíčku nainstalované aplikace na připojeném Xbox, HoloLens a IoT zařízení poprvé, Visual Studio nainstaluje správnou verzi vzdáleného ladicího programu pro cílové zařízení. Instalace vzdáleného ladicího programu může trvat nějakou dobu a zpráva **spouští se vzdálený ladicí program** , zobrazí se děje.

>[!NOTE]
>V současné době Xbox nebo HoloLens zařízení restartuje aplikaci v ladicím programu připojená, pokud byl již spuštěn.

Další informace o vzdálené nasazení aplikací pro UWP, naleznete v tématu [nasazení a ladění aplikací pro UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) a [aplikací pro UWP ladění na vzdálených počítačích](run-windows-store-apps-on-a-remote-machine.md). 
  
## <a name="see-also"></a>Viz také:  
 [Ladění v sadě Visual Studio](../debugger/index.md)  
 [Prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)  
 [Vzdálené ladění](../debugger/remote-debugging.md)  
 [Konfigurace brány firewall ve Windows pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)  
 [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)