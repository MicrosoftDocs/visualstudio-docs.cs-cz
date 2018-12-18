---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1abff9f393b34bbf5950c9e56b6f489f332840db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113244"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Pomocí modul ladění (DE) spusťte a ukončete programy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno modulem vlastní DE, pokud má zvláštní požadavky na spuštění procesu, který nemůže zpracovávat zcela vlastní port. To je obvykle případě, když je DE je součástí překladač a proces laděné je skript: překladač musí být nejprve spuštěn, a poté je skript načíst a spustit. Port můžete spustit Překladač, ale skript může vyžadovat zvláštní zpracování (což je, kde je DE má roli). Toto rozhraní je implementováno pouze v případě, že existují jedinečné požadavky pro spuštění programu, který nemůže zpracovávat vlastní port.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je volána správcem ladicí relace (SDM) Pokud SDM může toto rozhraní z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) rozhraní (použití QueryInterface). Pokud toto rozhraní můžete získat, SDM ví, že je DE má zvláštní požadavky a volá toto rozhraní ke spuštění programu místo nutnosti port spustíte.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugEngineLaunch2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Spustí proces prostřednictvím DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Obnoví zpracování provádění.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Určuje, pokud lze ukončit proces.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Ukončení procesu.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)