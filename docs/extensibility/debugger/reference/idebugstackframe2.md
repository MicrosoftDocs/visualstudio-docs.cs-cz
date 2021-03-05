---
description: Toto rozhraní představuje jeden rámec zásobníku v zásobníku volání v konkrétním vlákně.
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5ec53e89afb43187c641058620df53c4a61d6cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145908"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Toto rozhraní představuje jeden rámec zásobníku v zásobníku volání v konkrétním vlákně.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo rámec zásobníku.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Zavolejte [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pro načtení rozhraní [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) . Zavolejte na [Další](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) a načtěte strukturu [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , která obsahuje `IDebugStackFrame2` rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugStackFrame2` .

|Metoda|Popis|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Získá kontext kódu pro tento rámec zásobníku.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Získá kontext dokumentu pro tento rámec zásobníku.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Získá název rámce zásobníku.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Získá popis rámce zásobníku.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Načte reprezentace rozsahu fyzických adres spojených s rámcem zásobníku, která je závislá na počítači.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Získá kontext vyhodnocení pro vyhodnocení výrazu v rámci aktuálního kontextu rámce zásobníku a vlákna.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Získá jazyk spojený s rámcem zásobníku.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Získá popis vlastností spojených s rámcem zásobníku.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Vytvoří enumerátor pro vlastnosti rámce zásobníku.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Získá vlákno spojené s rámcem zásobníku.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní se získá jenom v případě, že se ladicí program zastavil na zarážce (buď způsobené zarážkou uživatele, nebo výjimku). Z tohoto rozhraní lze získat kontext výrazu pro vyhodnocení výrazů, může být vrácen seznam registrů nebo lze získat a prozkoumat zásobník volání.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
