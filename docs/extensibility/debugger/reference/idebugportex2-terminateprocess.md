---
description: 'IDebugPortEx2:: TerminateProcess ukončí proces.'
title: 'IDebugPortEx2:: TerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::TerminateProcess
helpviewer_keywords:
- IDebugPortEx2::TerminateProcess
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb783615ae50f8a3bb346e7d6aa281124104253e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072465"
---
# <a name="idebugportex2terminateprocess"></a>IDebugPortEx2::TerminateProcess
Ukončí proces.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
int TerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>Parametry
`pPortProcess`\
pro Objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) představující proces, který má být ukončen.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
