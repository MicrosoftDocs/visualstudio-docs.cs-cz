---
description: Používáno ladicím modulem (DE) pro spouštění a ukončování programů.
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8931590ea20373b5350d880d5fe9495dfe53c4f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077379"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Používáno ladicím modulem (DE) pro spouštění a ukončování programů.

## <a name="syntax"></a>Syntax

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastním nástrojem DE, pokud má zvláštní požadavky na spuštění procesu, který nelze zcela zpracovat vlastním portem. Obvykle se jedná o případ, kdy je DE součástí překladače a proces, který se právě ladí, je skript: je třeba nejprve spustit překladač a poté skript načíst a spustit. Port může spustit překladač, ale skript může vyžadovat speciální zpracování (kde DE má roli role). Toto rozhraní je implementováno pouze v případě, že existují jedinečné požadavky na spuštění programu, který vlastní port nemůže zpracovat.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se volá pomocí Správce ladění relace (SDM), pokud model SDM může získat toto rozhraní z rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (pomocí QueryInterface). Pokud je možné toto rozhraní získat, model SDM ví, že má zvláštní požadavky, a volá toto rozhraní, aby spustil program místo toho, aby port spouštěl.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugEngineLaunch2` .

|Metoda|Popis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Spustí proces pomocí prostředku DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Obnoví provádění procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Určuje, zda může být proces ukončen.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Ukončí proces.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
