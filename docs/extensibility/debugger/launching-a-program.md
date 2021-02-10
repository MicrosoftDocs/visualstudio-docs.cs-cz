---
title: Spuštění programu | Microsoft Docs
description: Přečtěte si o řadě událostí, ke kterým dochází při ladění programu pomocí klávesy F5 ke spuštění ladicího programu z integrovaného vývojového prostředí (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de29b012914ac9997a78674fd3215f2c15d43c6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945913"
---
# <a name="launch-a-program"></a>Spustit program
Uživatelé, kteří chtějí ladit program, mohou stisknout klávesu **F5** ke spuštění ladicího programu z integrovaného vývojového prostředí (IDE). Tím se spustí řada událostí, které nakonec mají za následek připojení rozhraní IDE k ladicímu stroji (DE), který je zase připojen nebo připojen k programu následujícím způsobem:

1. Rozhraní IDE nejprve zavolá balíček projektu, aby získalo nastavení ladění aktivního projektu v řešení. Mezi tato nastavení patří spouštěcí adresář, proměnné prostředí, port, ve kterém se program spustí, a příkaz DE k vytvoření programu, pokud je zadaný. Tato nastavení jsou předána balíčku pro ladění.

2. Je-li zadán parametr DE, příkaz DE zavolá operační systém, který spustí program. V důsledku spuštění programu se zatížení v prostředí programu runtime spustí. Například pokud je program napsán v jazyce MSIL, modul CLR (Common Language Runtime) bude vyvolán za účelem spuštění programu.

    -nebo-

    Pokud není zadán parametr DE, zavolá port operační systém, aby spustil program, což způsobí, že prostředí runtime programu bude načteno.

   > [!NOTE]
   > Je-li ke spuštění programu použit příkaz DE, je pravděpodobně k programu připojen stejný příkaz DE.

3. V závislosti na tom, jestli port DE nebo port spustil program, se v prostředí nástroje DE nebo run-time vytvoří Popis programu nebo uzel a upozorní port, na který program běží.

   > [!NOTE]
   > Doporučuje se, aby prostředí za běhu vytvořilo uzel programu, protože uzel programu je zjednodušená reprezentace programu, který se dá ladit. Není nutné načítat celou kopii jen pro vytvoření a registraci uzlu programu. Pokud je DE navržena tak, aby běžela v procesu rozhraní IDE, ale ve skutečnosti není spuštěno žádné integrované vývojové prostředí, musí být součástí, která může přidat uzel programu do portu.

   Nově vytvořený program, společně s dalšími programy, souvisejícími nebo nesouvisejícími, spuštěnými nebo připojenými ke stejnému prostředí IDE, tvoří relaci ladění.

   Programově, když uživatel poprvé stiskne **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] balíček ladění volá balíček projektu (který je přidružen k typu spouštěného programu) prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody, která zase vyplní <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> strukturu s nastavením ladění aktivní projekt v řešení. Tato struktura je předána zpět do ladicího balíčku prostřednictvím volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metody. Ladicí balíček potom vytvoří instanci správce ladění relace (SDM), která spustí laděný program a všechny přidružené ladicí moduly.

   Jedním z argumentů předaných metodě SDM je identifikátor GUID DE, který se má použít ke spuštění programu.

   Pokud identifikátor GUID není `GUID_NULL` , model SDM vytvoří příkaz de a pak zavolá jeho metodu [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pro spuštění programu. Například pokud je program napsán v nativním kódu, `IDebugEngineLaunch2::LaunchSuspended` bude pravděpodobně volána `CreateProcess` a `ResumeThread` (funkce Win32) pro spuštění programu.

   V důsledku spuštění programu se načte prostředí modulu runtime v čase programu. V prostředí DE nebo prostředí za běhu pak vytvoří rozhraní [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) k popisu programu a předá toto rozhraní [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) , aby upozornilo na port, na kterém je program spuštěný.

   Pokud `GUID_NULL` je předán, port spustí program. Po spuštění programu vytvoří prostředí za běhu `IDebugProgramNode2` rozhraní pro popis programu a předává ho do `IDebugPortNotify2::AddProgramNode` . Tím se upozorní port, na kterém je program spuštěný. Pak SDM připojí ladicí modul ke spuštěnému programu.

## <a name="in-this-section"></a>V této části
 [Oznamování portu](../../extensibility/debugger/notifying-the-port.md) Vysvětluje, co se stane po spuštění programu a upozornění na port.

 [Připojení po spuštění](../../extensibility/debugger/attaching-after-a-launch.md) Dokumenty, když je relace ladění připravena k připojení příkazu DE k programu.

## <a name="related-sections"></a>Související oddíly
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
