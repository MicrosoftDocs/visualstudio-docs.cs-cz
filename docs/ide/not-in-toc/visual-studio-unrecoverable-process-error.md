---
title: Při procesu došlo k neopravitelné chybě.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585792"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Chyba procesu neopravitelného v sadě Visual Studio

Visual Studio používá několik procesů mimo proc ke spuštění požadovaných úloh na pozadí, jako je například testování živých částí, analyzátory kódu a další. Tyto procesy jsou spuštěny out-of-of-proc poskytnout Visual Studio výhody výkonu, jako je například povolení Visual Studio reagovat rychleji při spuštění dlouhé úlohy náročné na prostředky. Také vzhledem k tomu, že Visual Studio je 32bitový proces, spouštění procesů mimo proc poskytuje práci náročné na paměť větší paměťový prostor, ve kterém chcete pracovat.

Pokud *serviceHub.RoslynCodeAnalysis.exe* nebo *ServiceHub.RoslynCodeAnalysisService32.exe* proces skončí z nějakého důvodu, rozbalovací informační panel se zobrazí s následující zprávou:

**"Bohužel proces používaný visual studio došlo k neopravitelné chybě. Doporučujeme uložit práci a potom zavřít a restartovat Visual Studio."**

Pokud se zobrazí tato zpráva, měli byste uložit práci a potom zavřít a restartovat Visual Studio.

## <a name="list-of-processes"></a>Seznam procesů

Následuje seznam procesů mimo proc používaných visual studio. Tento seznam zahrnuje procesy, které se spouštějí v konkrétních pracovních postupech nebo scénářích, a proto ve většině případů nejsou všechny spuštěny současně.

- Soubor Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- Služba ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Pokud některý z těchto procesů neočekávaně ukončí, některé funkce v rámci sady Visual Studio přestane fungovat. U některých procesů může být ztráta funkčnosti nevýznamná. Pro ostatní je ovlivněna stabilita sady Visual Studio a zobrazí se chybová zpráva.
