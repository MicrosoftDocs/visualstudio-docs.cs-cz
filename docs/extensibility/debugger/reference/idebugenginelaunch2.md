---
title: IDebugEngineLaunch2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730490"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Používá se ladicí modul (DE) ke spuštění a ukončení programů.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastní DE, pokud má zvláštní požadavky pro spuštění procesu, který nelze zcela zpracovat vlastní port. To je obvykle případ, kdy DE je součástí interpreta a proces, který je odladěn je skript: interpret musí být spuštěn nejprve a pak skript je načten a spuštěn. Port může spustit interpret, ale skript může vyžadovat zvláštní zpracování (což je místo, kde DE má roli). Toto rozhraní je implementováno pouze v případě, že existují jedinečné požadavky na spuštění programu, který vlastní port nelze zpracovat.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je voláno správcem ladění relace (SDM), pokud SDM může získat toto rozhraní z rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (pomocí QueryInterface). Pokud lze získat toto rozhraní, SDM ví, že DE má zvláštní požadavky a volá toto rozhraní ke spuštění programu namísto spuštění portu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEngineLaunch2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Spustí proces pomocí DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Obnoví provádění procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Určuje, zda lze proces ukončit.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Ukončí proces.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
