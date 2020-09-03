---
title: 'IDebugAddress2:: GetProcessId – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94873e9a9c05a0c5e9253ce53240ab6b4ca39064
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736586"
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
