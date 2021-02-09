---
title: 'IDebugProgramHost2:: GetHostId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9fb207539cdc6a12819fad4f87c6da3540f1aba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898851"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Získává identifikátor procesu hostujícího tento program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostId( 
   AD_PROCESS_ID* pdwId
);
```

```csharp
int GetHostId( 
   AD_PROCESS_ID[] pdwId
);
```

## <a name="parameters"></a>Parametry
`pdwId`\
[in, out] Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , která je vyplněná informacemi o identifikátoru procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
