---
title: Visual Studio na zařízeních s procesorem ARM
description: Doporučení pro používání sady Visual Studio na zařízeních s procesory na bázi ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d42f16e62437eac856c63e5436f4d3243bbae004
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889769"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio na zařízeních s procesorem ARM

> [!IMPORTANT]
> Visual Studio se podporuje jenom na zařízeních, která používají procesor založený na platformě x86 nebo AMD64 nebo x64.

Visual Studio je postavené na procesory založené na architektuře x86 a nejsou k dispozici žádné verze sady Visual Studio pro procesory založené na ARM. Systém Windows však poskytuje [emulaci x86 na ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), kterou lze spustit v sadě Visual Studio. Spuštění sady Visual Studio na procesoru ARM přes emulaci x86 vážně přetěžuje výkon sady Visual Studio a několik funkcí v sadě Visual Studio není navrženo pro práci v tomto scénáři. V takovém případě nedoporučujeme spouštět Visual Studio na zařízeních, která používají procesory na bázi ARM, a místo toho doporučujeme vzdáleně cílit zařízení ARM.

## <a name="remote-targeting-arm-devices"></a>Vzdálené cílení zařízení ARM
Pro dosažení nejlepšího prostředí doporučujeme používat Visual Studio na samostatném počítači s procesorem x86, na kterém běží, a používat funkce vzdáleného nasazení a ladění v sadě Visual Studio k cílení na zařízení s procesorem ARM. Chcete-li ladit univerzální aplikace systému Windows, které jsou již nainstalovány na zařízení, přečtěte si dokumentaci k [balíčku nainstalovaná aplikace](../debugger/debug-installed-app-package.md) . Pokud chcete nasadit novou aplikaci, přečtěte si téma [spuštění aplikace pro Windows Store remotley](../debugger/run-windows-store-apps-on-a-remote-machine.md). Všechny ostatní typy aplikací naleznete v dokumentaci ke [vzdálenému ladění](../debugger/remote-debugging.md) .

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Tipy pro spuštění sady Visual Studio na zařízeních ARM

### <a name="use-only-when-needed"></a>Použijte pouze v případě potřeby
Optimalizujte čas použitím sady Visual Studio, pouze pokud je to nutné pro práci specifickou pro ARM. Výkon na jakémkoli zařízení s technologií ARM bude nízký a pravděpodobně zjistíte, že ho nepůjde použít k běžnému použití.

### <a name="install-time"></a>Čas instalace
Plán pro sadu Visual Studio, která bude trvat déle, než se nainstaluje a očekává se, že se pozastaví na časové období nebo bude vyžadovat restartování.
 
### <a name="remote-tools"></a>Vzdálené nástroje
Pokud chcete ladit aplikaci běžící na vzdáleném zařízení, budete muset [Stáhnout a nainstalovat nástroje Remote Tools](../debugger/remote-debugging.md#download-and-install-the-remote-tools) for ARM.

### <a name="start-debugging-f5"></a>Spustit ladění (F5)
Ne všechny projekty sady Visual Studio jsou nakonfigurovány tak, aby se projekty spouštěly místně při spuštění ladění (**F5**) ze zařízení ARM. Je možné, že budete muset nakonfigurovat aplikaci Visual Studio pro vzdálené ladění, i když vaše aplikace běží místně. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Potřebujeme vaši technickou podporu.
Pokud chcete, aby aplikace Visual Studio běžela nativně na zařízeních ARM, rádi bychom slyšeli o scénářích a podpoře, které jsou nezbytné. Můžete nás kontaktovat publikováním na [komunitě vývojářů](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html).
