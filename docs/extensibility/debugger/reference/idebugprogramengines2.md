---
description: Toto rozhraní se používá v uzlech programu k určení všech možných ladicích modulů (DE), které mohou ladit tento program.
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c19b4dc3967cf7001144d38114a1f873776cb2b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149584"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Toto rozhraní se používá v uzlech programu k určení všech možných ladicích modulů (DE), které mohou ladit tento program.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Nevlastní dodavatel portu implementuje toto rozhraní na stejný objekt, který implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pro podporu vytvoření KONKRÉTNÍho de pro použití pro konkrétní program.

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugProgramNode2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProgramEngines2` .

|Metoda|Popis|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Označuje všechny možné DEs, které mohou ladit tento program.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Vybere DE, který má být použit pro ladění tohoto programu.|

## <a name="remarks"></a>Poznámky
 Jakmile uživatel vybere DE, je tato volba registrována v uzlu program voláním [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Vybraný modul se stal modulem vráceným funkcí [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
