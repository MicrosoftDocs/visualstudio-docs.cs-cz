---
title: Spuštění programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738474"
---
# <a name="launch-a-program"></a>Spuštění programu
Uživatelé, kteří chtějí ladit program můžete stisknout **F5** spustit ladicí program z IDE. To začíná řadu událostí, které nakonec za následek IDE připojení k ladicí modul (DE), který je zase připojen nebo připojen k programu takto:

1. IDE nejprve volá balíček projektu získat nastavení ladění aktivní ho řešení. Nastavení zahrnují počáteční adresář, proměnné prostředí, port, ve kterém bude program spuštěn, a DE, který se použije k vytvoření programu, pokud je zadán. Tato nastavení jsou předány balíček ladění.

2. Pokud de je zadán, DE volá operační systém ke spuštění programu. V důsledku spuštění programu se načte prostředí za běhu programu. Například pokud je program zapsán v MSIL, bude vyvolána čas ový čas společného jazyka ke spuštění programu.

    -nebo-

    Pokud de není zadán, port volá operační systém ke spuštění programu, který způsobí, že program run-time prostředí načíst.

   > [!NOTE]
   > Pokud DE se používá ke spuštění programu, je pravděpodobné, že stejný DE bude připojen k programu.

3. V závislosti na tom, zda de nebo port spustil program, DE nebo run-time prostředí pak vytvoří popis programu nebo uzel a upozorní port, který je spuštěn program.

   > [!NOTE]
   > Doporučuje se, aby prostředí run-time vytvořilo uzel programu, protože uzel programu je zjednodušenou reprezentací programu, který lze ladit. Není třeba načítat celý DE jen vytvořit a zaregistrovat uzel programu. Pokud DE je určen ke spuštění v procesu ide, ale žádné ide je ve skutečnosti spuštěna, musí být součást, která můžete přidat uzel programu na port.

   Nově vytvořený program, spolu s jinými programy, související nebo nesouvisející, spuštěné nebo připojené ze stejného IDE, tvoří ladicí relaci.

   Programově, když uživatel poprvé stiskne **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]'s ladicí balíček volá balíček projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (který je spojen s <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> typem programu, který je spuštěn) prostřednictvím metody, která zase vyplní strukturu s aktivním nastavením ladění projektu. Tato struktura je předána zpět do balíčku <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> ladění prostřednictvím volání metody. Ladicí balíček pak vytvoří instance správce ladění relace (SDM), který spustí program, který je laděný a všechny přidružené ladicí motory.

   Jedním z argumentů předaných SDM je identifikátor GUID de, který má být použit ke spuštění programu.

   Pokud DE GUID `GUID_NULL`není , SDM co-vytvoří DE a potom volá jeho [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metoda ke spuštění programu. Například pokud je program napsán v `IDebugEngineLaunch2::LaunchSuspended` nativním kódu, bude pravděpodobně volat `CreateProcess` a `ResumeThread` (Win32 funkce) ke spuštění programu.

   V důsledku spuštění programu je načteno prostředí běhu programu. De nebo run-time prostředí pak vytvoří rozhraní [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) k popisu programu a předá toto rozhraní [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) upozornit port, který je spuštěn program.

   Pokud `GUID_NULL` je předán, pak port spustí program. Jakmile je program spuštěn, prostředí run-time vytvoří `IDebugProgramNode2` rozhraní popisující program `IDebugPortNotify2::AddProgramNode`a předá jej aplikaci . To upozorní port, který je spuštěn program. Potom SDM připojí ladicí modul spuštěný program.

## <a name="in-this-section"></a>V tomto oddílu
 [Upozornění na port](../../extensibility/debugger/notifying-the-port.md) Vysvětluje, co se stane po spuštění programu a port je upozorněn.

 [Připojení po startu](../../extensibility/debugger/attaching-after-a-launch.md) Dokumenty, když ladicí relace je připraven a připojit DE k programu.

## <a name="related-sections"></a>Související oddíly
 [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.
