---
description: Načte ID procesu, který vlastní objekt reprezentovaný tímto IDebugAddress2 rozhraním.
title: 'IDebugAddress2:: GetProcessId – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd7665af4f88c695dd74b51293da3eced3861230
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059194"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Načte ID procesu, který vlastní objekt reprezentovaný tímto [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) rozhraním.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Parametry
`pProcID`\
mimo ID procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
