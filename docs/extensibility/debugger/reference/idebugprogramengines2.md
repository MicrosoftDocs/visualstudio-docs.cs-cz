---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722397"
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
 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

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
