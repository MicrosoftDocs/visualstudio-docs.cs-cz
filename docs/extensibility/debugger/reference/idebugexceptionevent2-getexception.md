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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72457b1b8931d028f555e7f9354f34b133fa79bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084776"
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
