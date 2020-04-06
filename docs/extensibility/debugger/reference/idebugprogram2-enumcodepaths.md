---
title: IDebugProgram2::EnumCodePaths | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723032"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Načte seznam cest kódu pro danou pozici ve zdrojovém souboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parametry
`pszHint`\
[v] Slovo pod kurzorem v pohledu **Zdroj** nebo **Demontáž** v ide.

`pStart`\
[v] Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující aktuální kontext kódu.

`pFrame`\
[v] [Objekt IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) představující rámec zásobníku přidružený k aktuální zarážky.

`fSource`\
[v] Nenulová`TRUE`( ), pokud je v`FALSE`pohledu **Zdroj,** nebo nula ( ), pokud je v pohledu **demontáže.**

`ppEnum`\
[out] Vrátí objekt [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obsahující seznam cest kódu.

`ppSafety`\
[out] Vrátí objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující kontext dalšího kódu, který má být nastaven jako zarážka v případě, že je přeskočena zvolená cesta kódu. K tomu může dojít například v případě zkráceného logického výrazu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Cesta kódu popisuje název metody nebo funkce, která byla volána k získání aktuálního bodu při provádění programu. Seznam cest kódu představuje zásobník volání.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
