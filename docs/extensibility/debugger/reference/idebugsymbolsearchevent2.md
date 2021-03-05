---
description: Toto rozhraní se posílá ladicím modulem (DE), aby označovalo, že se načetly ladicí symboly pro modul, který se právě ladí.
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ef2d315568b78e567d682728c4cbc989c5a4ed2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145739"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Toto rozhraní se posílá ladicím modulem (DE), aby označovalo, že se načetly ladicí symboly pro modul, který se právě ladí.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že byly načteny symboly modulu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, aby nahlásila, že byly načteny symboly modulu. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojen k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 `IDebugSymbolSearchEvent2`Rozhraní zpřístupňuje následující metodu.

|Metoda|Popis|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Načte informace o výsledcích hledání symbolů.|

## <a name="remarks"></a>Poznámky
 Tato událost bude odeslána i v případě, že se symboly nepodařilo načíst. Volání `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` umožňuje obslužné rutině této události určit, jestli má modul ve skutečnosti nějaké symboly.

 Visual Studio obvykle používá tuto událost k aktualizaci stavu načtených symbolů v okně **moduly** .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
