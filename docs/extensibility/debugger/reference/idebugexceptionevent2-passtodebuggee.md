---
title: IDebugExceptionEvent2::PassToDebuggee | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729829"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Určuje, zda má být výjimka předána programu, který je laděn při obnovení provádění, nebo zda má být výjimka zahozena.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parametry
`fPass`\
[v] Nenulová`TRUE`( ), pokud by měla být výjimka předána programu, který`FALSE`je laděn při obnovení provádění, nebo nula ( ), pokud by měla být výjimka zahozena.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Volání této metody ve skutečnosti nezpůsobí spuštění žádného kódu v ladicím programu. Volání je pouze nastavit stav pro další spuštění kódu. Například volání [Metody CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) může `S_OK` vrátit s [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` pole nastaveno na `EXCEPTION_STOP_SECOND_CHANCE`.

 IDE může přijímat událost [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) a volat metodu [Continue.](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Ladicí modul (DE) by měl mít výchozí `PassToDebuggee` chování pro zpracování případu, pokud není volána metoda.

## <a name="see-also"></a>Viz také
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
