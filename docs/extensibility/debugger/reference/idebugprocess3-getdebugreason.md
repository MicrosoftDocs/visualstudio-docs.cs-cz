---
description: Tato metoda vrací důvod, proč byl proces spuštěn pro ladění.
title: 'IDebugProcess3:: GetDebugReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c015756b441dacbd86be0c562c859753b7c8903b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081565"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Tato metoda vrací důvod, proč byl proces spuštěn pro ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

## <a name="parameters"></a>Parametry
`pReason`\
mimo Vrací hodnotu z výčtu [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)
