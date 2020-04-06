---
title: IDebugProgram2::EnumCodeContexts | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22a5ce398e76ee97b2f0448900fd4e38f996615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723047"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Načte seznam kontextů kódu pro danou pozici ve zdrojovém souboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`pDocPos`\
[v] Objekt [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) představující abstraktní pozici ve zdrojovém souboru známém ide.

`ppEnum`[out] Vrátí objekt [IEnumDebugCodeContexts2,](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) který obsahuje seznam kontextů kódu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda umožňuje správce ladění relace (SDM) nebo IDE mapovat umístění zdrojového souboru do pozice kódu. Více než jeden kontext kódu je vrácena, pokud zdroj generuje více bloků kódu (například šablony C++).

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
