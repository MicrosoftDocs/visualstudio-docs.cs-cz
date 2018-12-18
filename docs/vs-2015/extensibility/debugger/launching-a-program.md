---
title: Spuštění programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3af2c1f571287a4a33c1dd57340e2a66197bd59
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753952"
---
# <a name="launching-a-program"></a>Spuštění programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uživatelé, kteří chtějí ladění programu, můžete stisknutím klávesy F5 spusťte ladicí program v prostředí IDE. Tím se zahájí řadu událostí, takže v konečném důsledku vzniklé v rozhraní IDE propojíte ladicího stroje (DE), který je zase připojení nebo připojení k programu následujícím způsobem:  
  
1. Rozhraní IDE nejprve volá balíček projektu zobrazíte nastavení pro ladění aktivní projekt řešení. Nastavení zahrnují spouštěcí adresář, proměnné prostředí, port, ve kterém se spustí program a DE použít k vytvoření programu, pokud zadaný. Tato nastavení jsou předány do balíčku pro ladění.  
  
2. Pokud není zadána Německo, DE volá operačního systému spustit program. V důsledku spuštění programu, je načtení prostředí za běhu programu. Například pokud je program napsán v jazyce MSIL, modul common language runtime bude vyvoláno pro spuštění programu.  
  
    -nebo-  
  
    Pokud není zadán Zavedenými, port, který volá operačního systému spustit program, což způsobí, že prostředí za běhu programu načíst.  
  
   > [!NOTE]
   >  Pokud se Zavedenými používá ke spuštění programu, je pravděpodobné, že stejné DE bude připojen k programu.  
  
3. V závislosti na tom, zda je DE nebo port, který spustil program DE nebo běhové prostředí potom vytvoří popis programu, nebo uzel a upozorní port, který je spuštěn program.  
  
   > [!NOTE]
   >  Doporučuje, běhové prostředí vytvořit uzel program, protože uzel programu je zjednodušené reprezentace program, který lze ladit. Není nutné načíst si celé DE jenom k vytvoření a registrace uzlu programu. Pokud je DE je navržená ke spuštění procesu prostředí IDE, ale bez integrovaného vývojového prostředí je ve skutečnosti spuštěn, musí být součást, která můžete přidat uzel, program na port.  
  
   Nově vytvořený program, společně s další programy, související nebo nesouvisející, spuštění nebo připojené k ze stejného prostředí IDE, vytvořte relaci ladění.  
  
   Prostřednictvím kódu programu, když uživatel nejprve stiskne **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]společnosti ladit balíček volá balíček projektu (které je spojeno s typem spuštění programu) prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodu, která zase vyplní <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> strukturu pomocí nastavení pro ladění aktivní projekt řešení. Tato struktura je předán zpět do balíčku pro ladění přímo pomocí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metody. Ladění balíčku poté vytvoří instanci správce ladění relace (SDM), který spouští program právě laděny a všechny přidružené ladicí stroj.  
  
   Jeden z argumentů předaných SDM je identifikátor GUID DE, který se má použít ke spuštění programu.  
  
   Pokud je identifikátor GUID DE `GUID_NULL`, SDM společně vytvoří DE a pak zavolá jeho [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodu spustit program. Například, pokud je program napsán v nativním kódu, pak `IDebugEngineLaunch2::LaunchSuspended` pravděpodobně zavolá `CreateProcess` a `ResumeThread` (funkce Win32) ke spuštění programu.  
  
   V důsledku spuštění programu, je načtení prostředí za běhu programu. DE nebo běhové prostředí vytvoří [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) rozhraní pro popis programu a předává tohoto rozhraní [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) sdělit port, který je program spuštění.  
  
   Pokud `GUID_NULL` je předán, a port, který spouští program. Po spuštění programu vytvoří prostředí za běhu `IDebugProgramNode2` rozhraní pro popis programu a předává jej do `IDebugPortNotify2::AddProgramNode`. To upozorní port, který program je spuštěn. Potom SDM připojí ke spuštěnému programu ladicí stroj.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Upozornění portu](../../extensibility/debugger/notifying-the-port.md)  
 Vysvětluje, co se stane po spuštění programu a port, který obdrží oznámení.  
  
 [Připojení po spuštění](../../extensibility/debugger/attaching-after-a-launch.md)  
 Dokumenty při relaci ladění je připraven k DE připojit k programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.

