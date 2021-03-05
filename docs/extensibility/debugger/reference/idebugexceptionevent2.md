---
description: Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), když je v aktuálně zpracovávaném programu vyvolána výjimka.
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e171154d933ac533f6a63469321b5a0d22e8651b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152764"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), když je v aktuálně zpracovávaném programu vyvolána výjimka.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že došlo k výjimce v laděném programu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, aby hlásil výjimku. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána službou SDM, když je připojená k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugExceptionEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Získá podrobné informace o výjimce, která vyvolala tuto událost.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Získá popis pro vyvolané výjimky, která vyvolala tuto událost.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Určuje, zda ladicí stroj (DE) podporuje možnost předávání této výjimky do programu laděného v okamžiku, kdy provádění pokračuje.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Určuje, zda má být výjimka předána do programu laděného v případě, že spuštění pokračuje nebo zda by měla být výjimka zahozena.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Poznámky
 Před odesláním události DE zkontroluje, zda byla tato událost výjimky označena jako první nebo druhá výjimka při předchozím volání [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Pokud byl navržen jako výjimka první pravděpodobnost, bude `IDebugExceptionEvent2` událost odeslána na SDM. V takovém případě DE udělí aplikaci možnost zpracovat výjimku. Pokud není k dispozici žádná obslužná rutina výjimky a pokud byla výjimka určena jako výjimka druhé pravděpodobnosti, `IDebugExceptionEvent2` je událost odeslána na SDM. V opačném případě příkaz DE obnoví provádění programu a operační systém nebo modul runtime zpracuje výjimku.

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
