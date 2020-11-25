---
title: Došlo k neopravitelné chybě procesu.
description: Přečtěte si o procesech, které se můžou setkat s neodstranitelnými chybami při normálním provozu sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e44f96e0a8056a369b164e725aca6832b5a349cb
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871480"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Chyba neodstranitelné procesu sady Visual Studio

Visual Studio používá několik procesů mimo procesy ke spouštění požadovaných úloh na pozadí, jako je Live Unit Testing, analyzátory kódu a další. Tyto procesy jsou spouštěny mimo proc, aby poskytovaly výhody výkonu sady Visual Studio, jako je například umožnění rychlejší reakce sady Visual Studio při spuštění dlouhotrvajících úloh náročných na prostředky. Vzhledem k tomu, že Visual Studio je 32 proces, spuštěné procesy mimo proc poskytují paměť náročné na velikost paměti, ve které je možné pracovat.

Pokud proces *ServiceHub.RoslynCodeAnalysisService.exe* nebo *ServiceHub.RoslynCodeAnalysisService32.exe* z nějakého důvodu končí, zobrazí se automaticky otevírané okno s následující zprávou:

**"Omlouváme se, ale proces používaný v aplikaci Visual Studio narazil na neodstranitelnou chybu. Doporučujeme uložit práci a potom zavřít a restartovat aplikaci Visual Studio. "**

Pokud se zobrazí tato zpráva, měli byste uložit svoji práci a pak zavřít a restartovat aplikaci Visual Studio.

## <a name="list-of-processes"></a>Seznam procesů

Následuje seznam procesů, které používá aplikace Visual Studio. Tento seznam zahrnuje procesy, které se spouštějí v konkrétních pracovních postupech nebo scénářích, a to ve většině případů, kdy nejsou spuštěné ve stejnou dobu.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft. CodeAnalysis. LiveUnitTesting. EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Pokud některý z těchto procesů skončí neočekávaně, některé funkce v sadě Visual Studio přestanou fungovat. U některých procesů může být ztráta funkčnosti nevýznamná. Pro jiné je ovlivněna stabilita sady Visual Studio a zobrazí se chybová zpráva.

> [!NOTE]
> Pokud se setkáte s problémem, který na této stránce neodkazuje, ohlaste ho prosím přes Nástroj pro [nahlášení problému](../../ide/how-to-report-a-problem-with-visual-studio.md) , který se zobrazí v instalační program pro Visual Studio i v integrovaném vývojovém prostředí sady Visual Studio.
