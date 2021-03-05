---
description: 'IDebugFunctionObject2:: Evaluate volá funkci a vrátí výslednou hodnotu jako objekt.'
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 777553e1889e751cf84f6e4c58691e0c5f446648
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166460"
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
pro Pole objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , které představují vstupní parametry. Každý z těchto parametrů byl vytvořen pomocí jedné z metod Create v tomto rozhraní.

`dwParams`\
pro Počet parametrů v `ppParams` poli.

`dwEvalFlags`\
pro Kombinace příznaků z výčtu [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , která určuje, jak má být provedeno vyhodnocení.

`dwTimeout`\
pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Nepoužívejte **nekonečné** čekání na neomezenou dobu.

`ppResult`\
mimo Vrátí **IDebugObject** , který představuje hodnotu funkce jako objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
