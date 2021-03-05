---
description: Získá podrobný popis výjimky, která aktivovala tuto událost.
title: 'IDebugExceptionEvent2:: gets výjimkou | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6505cd2309323d7fe91f2c807af33555c3575fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152894"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Získá podrobný popis výjimky, která aktivovala tuto událost.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parametry
`pExceptionInfo`\
[in, out] Struktura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , která je vyplněna s popisem výjimky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky

 [Pouze C++] Volající je zodpovědný za uvolnění všech řetězců ve struktuře [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) a uvolnění objektu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ve struktuře.

## <a name="see-also"></a>Viz také
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
