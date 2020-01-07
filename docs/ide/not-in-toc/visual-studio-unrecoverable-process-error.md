---
title: Došlo k neopravitelné chybě procesu.
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206fcddca51f8e770e013ff67de6ae3d5562f633
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585792"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Chyba neodstranitelné procesu sady Visual Studio

Visual Studio používá několik procesů mimo procesy ke spouštění požadovaných úloh na pozadí, jako je Live Unit Testing, analyzátory kódu a další. Tyto procesy jsou spouštěny mimo proc, aby poskytovaly výhody výkonu sady Visual Studio, jako je například umožnění rychlejší reakce sady Visual Studio při spuštění dlouhotrvajících úloh náročných na prostředky. Vzhledem k tomu, že Visual Studio je 32 proces, spuštěné procesy mimo proc poskytují paměť náročné na velikost paměti, ve které je možné pracovat.

Pokud se z nějakého důvodu ukončí proces *ServiceHub. RoslynCodeAnalysisService. exe* nebo *ServiceHub. RoslynCodeAnalysisService32. exe* , zobrazí se automaticky otevírané okno s následující zprávou:

**"Omlouváme se, ale proces používaný v aplikaci Visual Studio narazil na neodstranitelnou chybu. Doporučujeme uložit práci a potom zavřít a restartovat aplikaci Visual Studio. "**

Pokud se zobrazí tato zpráva, měli byste uložit svoji práci a pak zavřít a restartovat aplikaci Visual Studio.

## <a name="list-of-processes"></a>Seznam procesů

Následuje seznam procesů, které používá aplikace Visual Studio. Tento seznam zahrnuje procesy, které se spouštějí v konkrétních pracovních postupech nebo scénářích, a to ve většině případů, kdy nejsou spuštěné ve stejnou dobu.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Pokud některý z těchto procesů skončí neočekávaně, některé funkce v sadě Visual Studio přestanou fungovat. U některých procesů může být ztráta funkčnosti nevýznamná. Pro jiné je ovlivněna stabilita sady Visual Studio a zobrazí se chybová zpráva.
