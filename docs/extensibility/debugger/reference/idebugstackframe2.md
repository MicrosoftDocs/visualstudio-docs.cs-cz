---
title: IDebugStackFrame2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719509"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Toto rozhraní představuje jeden rámec zásobníku v zásobníku volání v určitém vlákně.

## <a name="syntax"></a>Syntaxe

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující rámec zásobníku.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [enumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) načíst rozhraní [IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Volání [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) načíst [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strukturu, která obsahuje `IDebugStackFrame2` rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugStackFrame2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Získá kontext kódu pro tento rámec zásobníku.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Získá kontext dokumentu pro tento rámec zásobníku.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Získá název rámce zásobníku.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Získá popis rámce zásobníku.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Získá počítačově závislé reprezentace rozsahu fyzických adres spojených s rámcem zásobníku.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Získá kontext hodnocení pro provedení vyhodnocení výrazu v aktuálním kontextu rámce zásobníku a vlákna.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Získá jazyk přidružený k rámci zásobníku.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Získá popis vlastností spojených s rámcem zásobníku.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Vytvoří čítač výčtu pro vlastnosti rámce zásobníku.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Získá vlákno přidružené k rámci zásobníku.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je získáno pouze v případě, že program, který je laděn byl zastaven na zarážky (buď způsobené uživatelem nastavenou zarážkou nebo výjimkou). Z tohoto rozhraní lze získat kontext výrazu k vyhodnocení výrazů, seznam registrů lze vrátit nebo zásobník volání lze získat a zkontrolovány.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
