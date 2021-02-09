---
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b337d9c6742c1c3b0379a757761955151cc6dc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898655"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Získá název a identifikátor ladicího modulu (DE), který spouští program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametry
`pbstrEngine`\
mimo Vrátí název DE běhu programu (specifické pro C++: může to být ukazatel s hodnotou null, který značí, že volající nemá zájem o název modulu).

`pguidEngine`\
mimo Vrátí globálně jedinečný identifikátor při spuštění programu (specifický pro C++: může to být ukazatel s hodnotou null, který značí, že volající nemá zájem o identifikátor GUID modulu).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
