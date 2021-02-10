---
title: 'IDebugStackFrame3:: InterceptCurrentException – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8e3ef123fb88f1519d398952ed2d27de0fb0b91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963546"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Volá se ladicím programem v aktuálním bloku zásobníku, když chce zachytit aktuální výjimku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parametry
`dwFlags`\
pro Určuje různé akce. V současné době je podporována pouze hodnota [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) `IEA_INTERCEPT` a je třeba ji zadat.

`pqwCookie`\
mimo Jedinečná hodnota identifikující určitou výjimku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

 Níže jsou uvedené nejběžnější chyby.

|Chyba|Popis|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Aktuální výjimku nelze zachytit.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|V aktuálním snímku provádění nebyl dosud prohledána obslužná rutina.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Tato metoda není pro tento rámec podporována.|

## <a name="remarks"></a>Poznámky
 Když je vyvolána výjimka, ladicí program získá řízení z doby běhu v klíčových bodech během procesu zpracování výjimky. Během tohoto klíčového momentu může ladicí program požádat o aktuální rámec zásobníku, pokud rámec chce zachytit výjimku. Tímto způsobem je zachycená výjimka v podstatě průběžná obslužná rutina výjimky pro rámec zásobníku, i když tento rámec zásobníku nemá obslužnou rutinu výjimky (například blok try/catch v programovém kódu).

 Když ladicí program chce zjistit, zda by měla být výjimka zachycena, volá tuto metodu na aktuální objekt rámce zásobníku. Tato metoda zodpovídá za zpracování všech podrobností o výjimce. Pokud rozhraní [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) není implementováno nebo `InterceptStackException` Metoda vrátí jakoukoli chybu, ladicí program pokračuje ve zpracování výjimky normálně.

> [!NOTE]
> Výjimky se můžou zachytit jenom ve spravovaném kódu, to znamená, že když je program laděný, běží v době běhu rozhraní .NET. Implementací jazyků třetích stran je samozřejmě možné implementovat `InterceptStackException` ve vlastních ladicích modulech, pokud si je zvolíte.

 Po dokončení zachycení se [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signál.

## <a name="see-also"></a>Viz také
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
