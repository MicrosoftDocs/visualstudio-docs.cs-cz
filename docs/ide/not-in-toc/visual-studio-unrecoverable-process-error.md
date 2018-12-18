---
title: Procesu došlo k neopravitelné chybě
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b6d69aa899ffea95c8da7c3513c6f7b0fa6002ee
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895155"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Chyba neopravitelné procesu Visual Studio

Visual Studio 2017 používá několik procesů v režimu out-of-proc pro spouštění úloh na pozadí povinné, jako je například živé testování částí, kód analyzátorů a dalších. Tyto procesy jsou spuštěny na více instancí proc poskytnout výhody výkonu sady Visual Studio, jako například povolení Visual Studio a rychleji reagovat při spuštění úlohy náročné na dlouho. Navíc vzhledem k tomu, že Visual Studio je 32bitový proces, spouštění procesy režimu out-of-proc poskytuje práce náročné na paměť větší paměťový prostor, ve kterém chcete pracovat.

Pokud *ServiceHub.RoslynCodeAnalysisService.exe* nebo *ServiceHub.RoslynCodeAnalysisService32.exe* ukončení procesu z nějakého důvodu se zobrazí automaticky otevírané informační panel s následující zprávou:

**"Bohužel proces využívaný sadou Visual Studio došlo k neodstranitelné chybě. Doporučujeme uložit vaši práci a pak ukončit a znovu spustit sadu Visual Studio."**

Pokud se zobrazí tato zpráva, by měl uložte svou práci a pak zavřete a restartujte aplikaci Visual Studio.

## <a name="list-of-processes"></a>Seznam procesů

Tady je seznam procesů režimu out-of-proc používá sada Visual Studio. Je tento seznam zahrnuje procesy, které budou spuštěny v určité pracovní postupy nebo scénáře, a to ve většině případů se nejsou všechny spuštěné ve stejnou dobu.

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

Pokud některý z těchto procesů neočekávaně ukončí, některé funkce v sadě Visual Studio přestane fungovat. Pro některé procesy může být neplatné ke ztrátě funkčnosti. Pro ostatní uživatele ovlivňuje stabilitu sady Visual Studio a zobrazí se chybová zpráva.