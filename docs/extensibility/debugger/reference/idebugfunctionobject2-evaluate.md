---
title: IDebugFunctionObject2::Vyhodnotit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728445"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Volá funkci a vrátí výslednou hodnotu jako objekt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[v] Pole [iDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty, které představuje vstupní parametry. Každý z těchto parametrů byl vytvořen pomocí jedné z Create metody v tomto rozhraní.

`dwParams`\
[v] Počet parametrů v `ppParams` poli.

`dwEvalFlags`\
[v] Kombinace příznaků z výčtu [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) které určují, jak má být hodnocení provedeno.

`dwTimeout`\
[v] Určuje maximální dobu v milisekundách, po kterou se má čekat před návratem z této metody. Použití **INFINITE** čekat neomezeně dlouho.

`ppResult`\
[out] Vrátí **objekt IDebugObject,** který představuje hodnotu funkce jako objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
