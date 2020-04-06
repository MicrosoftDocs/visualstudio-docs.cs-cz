---
title: IDebugProviderProgramNode2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720679"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Toto rozhraní zařazuje rozhraní související s programem přes hranice procesu.

## <a name="syntax"></a>Syntaxe

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní na stejném objektu, který implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pro podporu zařazování rozhraní přes hranice procesu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` na rozhraní získat toto rozhraní. Pokud toto rozhraní nelze získat, DE nepodporuje zařazování rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Získá zadané rozhraní přes hranice procesu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je implementováno při spuštění de v samostatném prostoru procesu od programu, který je laděn: například při de je spuštěn v prostoru procesu Sady Visual Studio namísto prostoru procesu programu, který je laděn.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
