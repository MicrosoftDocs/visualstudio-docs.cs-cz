---
title: Oznamování portu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cf3969dda783882f24d02a748f345cdb66fe413
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64857986"
---
# <a name="notifying-the-port"></a>Upozornění portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po spuštění programu musí být port upozorněn následujícím způsobem:  
  
1. Když port obdrží nový uzel programu, pošle událost vytvoření programu zpátky do ladicí relace. Událost přenáší rozhraní, které představuje program.  
  
2. Ladicí relace se dotazuje programu na identifikátor ladicího modulu (DE), který se může připojit k.  
  
3. Relace ladění zkontroluje, zda je v seznamu povolených algoritmů DEs pro daný program. Relace ladění získá tento seznam z nastavení aktivního programu řešení, které bylo původně předáno balíčkem pro ladění.  
  
    Příkaz DE musí být v seznamu povolených, jinak se v programu DE nebude připojovat.  
  
   Programově, když port nejprve obdrží nový uzel programu, vytvoří rozhraní [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , které bude reprezentovat program.  
  
> [!NOTE]
> Nemělo by se zaměňovat s `IDebugProgram2` rozhraním vytvořeným později modulem ladění (de).  
  
 Port pošle událost vytvoření programu [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zpět do Správce ladění relace (SDM) prostřednictvím `IConnectionPoint` rozhraní com.  
  
> [!NOTE]
> To by nemělo být zaměněno s `IDebugProgramCreateEvent2` rozhraním, které je odesláno později pomocí de.  
  
 Spolu s samotným rozhraním událostí odesílá port rozhraní [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)a [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , která reprezentují port, proces a program. Volání SDM [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) Získá identifikátor GUID příkazu de, který může ladit program. Identifikátor GUID byl původně získán z rozhraní [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
 SDM zjistí, zda je v seznamu povolených algoritmů DEs. Model SDM získá tento seznam z nastavení aktivního programu řešení, které bylo původně předáno balíčkem pro ladění. Příkaz DE musí být v seznamu povolených nebo jinak nebude připojen k programu.  
  
 Jakmile je známa identita DE, je model SDM připraven ho připojit k programu.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění programu](../../extensibility/debugger/launching-a-program.md)   
 [Připojení po spuštění](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
