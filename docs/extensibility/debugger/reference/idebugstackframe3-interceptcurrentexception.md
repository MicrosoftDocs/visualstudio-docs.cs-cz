---
title: IDebugStackFrame3::InterceptCurrentException | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719491"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Volána ladicím programem v aktuálním rámci zásobníku, pokud chce zachytit aktuální výjimku.

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
[v] Určuje různé akce. V současné době [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) je `IEA_INTERCEPT` podporována pouze hodnota INTERCEPT_EXCEPTION_ACTION a musí být zadána.

`pqwCookie`\
[out] Jedinečná hodnota identifikující konkrétní výjimku.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

 Následují nejběžnější chyby vrací.

|Chyba|Popis|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Aktuální výjimku nelze zachytit.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Aktuální prováděcí rámec ještě nebyl prohledán pro obslužnou rutinu.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Tato metoda není pro tento snímek podporována.|

## <a name="remarks"></a>Poznámky
 Při vyvolání výjimky ladicí program získá kontrolu z doby běhu v klíčových bodech během procesu zpracování výjimek. Během těchto klíčových momentů ladicí program může požádat aktuální rámec zásobníku, pokud snímek chce zachytit výjimku. Tímto způsobem zachycené výjimky je v podstatě on-the-fly obslužná rutina výjimky pro rámec zásobníku, i v případě, že rámec zásobníku nemá obslužnou rutinu výjimky (například try/catch bloku v kódu programu).

 Když ladicí program chce vědět, pokud by měla být výjimka zachycena, volá tuto metodu na aktuální matný objekt rámce zásobníku. Tato metoda je zodpovědná za zpracování všech podrobností o výjimce. Pokud rozhraní [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) není implementováno nebo `InterceptStackException` metoda vrátí jakoukoli chybu, ladicí program pokračuje ve zpracování výjimky normálně.

> [!NOTE]
> Výjimky mohou být zachyceny pouze ve spravovaném kódu, to znamená, když je laděný program spuštěn v době spuštění rozhraní .NET. Samozřejmě implementátory jazyka třetích `InterceptStackException` stran můžete implementovat ve svých vlastních ladicích modulů, pokud se tak rozhodnou.

 Po dokončení zachycení je signalizováno [IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

## <a name="see-also"></a>Viz také
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
