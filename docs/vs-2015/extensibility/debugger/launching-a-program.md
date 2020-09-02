---
title: Spuštění programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b54250a54960f346f60c5d668755fb5d28ab376e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833005"
---
# <a name="launching-a-program"></a>Spuštění programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uživatelé, kteří chtějí ladit program, mohou stisknout klávesu F5 ke spuštění ladicího programu z integrovaného vývojového prostředí (IDE). Tím se spustí řada událostí, které nakonec mají za následek připojení rozhraní IDE k ladicímu stroji (DE), který je zase připojen nebo připojen k programu následujícím způsobem:  
  
1. Rozhraní IDE nejprve zavolá balíček projektu, aby získalo nastavení ladění aktivního projektu v řešení. Mezi tato nastavení patří spouštěcí adresář, proměnné prostředí, port, ve kterém se program spustí, a příkaz DE k vytvoření programu, pokud je zadaný. Tato nastavení jsou předána balíčku pro ladění.  
  
2. Je-li zadán parametr DE, příkaz DE zavolá operační systém, který spustí program. V důsledku spuštění programu se načte prostředí modulu runtime v čase programu. Například pokud je program napsán v jazyce MSIL, modul CLR (Common Language Runtime) bude vyvolán za účelem spuštění programu.  
  
    -nebo-  
  
    Pokud není zadán parametr DE, zavolá port operační systém a spustí program, což způsobí načtení spouštěcího prostředí programu.  
  
   > [!NOTE]
   > Je-li ke spuštění programu použit příkaz DE, je pravděpodobně k programu připojen stejný příkaz DE.  
  
3. V závislosti na tom, jestli port DE nebo port spustil program, se v prostředí nástroje DE nebo run-time vytvoří Popis programu nebo uzel a upozorní port, na který program běží.  
  
   > [!NOTE]
   > Doporučuje se, aby prostředí za běhu vytvořilo uzel programu, protože uzel programu je zjednodušená reprezentace programu, který se dá ladit. Není nutné načítat celou kopii jen pro vytvoření a registraci uzlu programu. Pokud je DE navržena tak, aby běžela v procesu rozhraní IDE, ale ve skutečnosti není spuštěno žádné integrované vývojové prostředí, musí být součástí, která může přidat uzel programu do portu.  
  
   Nově vytvořený program, společně s dalšími programy, souvisejícími nebo nesouvisejícími, spuštěnými nebo připojenými ke stejnému prostředí IDE, tvoří relaci ladění.  
  
   Programově, když uživatel poprvé stiskne **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] balíček ladění volá balíček projektu (který je přidružen k typu spouštěného programu) prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody, která zase vyplní <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> strukturu s nastavením ladění aktivní projekt v řešení. Tato struktura je předána zpět do ladicího balíčku prostřednictvím volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metody. Ladicí balíček potom vytvoří instanci správce ladění relace (SDM), která spustí laděný program a všechny přidružené ladicí moduly.  
  
   Jedním z argumentů předaných metodě SDM je identifikátor GUID DE, který se má použít ke spuštění programu.  
  
   Pokud identifikátor GUID není `GUID_NULL` , model SDM vytvoří příkaz de a pak zavolá jeho metodu [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pro spuštění programu. Například pokud je program napsán v nativním kódu, pak `IDebugEngineLaunch2::LaunchSuspended` bude pravděpodobně volána `CreateProcess` a `ResumeThread` (funkce Win32) pro spuštění programu.  
  
   V důsledku spuštění programu se načte prostředí modulu runtime v čase programu. V prostředí DE nebo prostředí za běhu pak vytvoří rozhraní [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) k popisu programu a předá toto rozhraní [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) , aby upozornilo na port, na kterém je program spuštěný.  
  
   Pokud `GUID_NULL` je předán, port spustí program. Po spuštění programu vytvoří prostředí za běhu `IDebugProgramNode2` rozhraní pro popis programu a předává ho do `IDebugPortNotify2::AddProgramNode` . Tím se upozorní port, na kterém je program spuštěný. Pak SDM připojí ladicí modul ke spuštěnému programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Upozornění portu](../../extensibility/debugger/notifying-the-port.md)  
 Vysvětluje, co se stane po spuštění programu a upozornění na port.  
  
 [Připojení po spuštění](../../extensibility/debugger/attaching-after-a-launch.md)  
 Dokumenty, když je relace ladění připravena k připojení příkazu DE k programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
