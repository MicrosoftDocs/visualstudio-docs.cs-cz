---
title: 'IDebugThread2:: getprogram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 083973c82a5f8b3c24480e0964f67faca1977a71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718713"
---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
Získá program, ve kterém je vlákno spuštěno.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgram ( 
   IDebugProgram2** ppProgram
);
```

```csharp
int GetProgram ( 
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>Parametry
`ppProgram`\
mimo Vrátí objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, ve kterém je toto vlákno spuštěno.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
