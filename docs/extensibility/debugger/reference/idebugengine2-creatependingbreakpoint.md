---
title: IDebugEngine2::CreatePendingBreakpoint | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731115"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Vytvoří čekající zarážku v ladicímodul (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parametry
`pBPRequest`\
[v] [Objekt IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) který popisuje čekající zarážku, kterou chcete vytvořit.

`ppPendingBP`\
[out] Vrátí objekt [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) který představuje čekající zarážku.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Obvykle vrátí, `E_FAIL` `pBPRequest` pokud parametr neodpovídá žádný jazyk podporovaný `pBPRequest` DE, pokud je parametr neplatný nebo neúplný.

## <a name="remarks"></a>Poznámky
Čekající zarážka je v podstatě kolekce všech informací potřebných k vytvoření vazby zarážky na kód. Čekající zarážka vrácená z této metody není vázána na kód, dokud není volána metoda [Bind.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

Pro každou čekající zarážku, kterou uživatel nastaví, zavolá správce ladění relace (SDM) tuto metodu v každém připojeném DE. Je na DE ověřit, že zarážka je platná pro programy spuštěné v tomto DE.

Když uživatel nastaví zarážku na řádku kódu, DE je volně vázat zarážku na nejbližší řádek v dokumentu, který odpovídá tomuto kódu. To umožňuje uživateli nastavit zarážku na prvním řádku víceřádkového příkazu, ale svázat jej na posledním řádku (kde je veškerý kód přiřazen v informacích o ladění).

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CProgram` tuto metodu pro jednoduchý objekt. DE implementace `IDebugEngine2::CreatePendingBreakpoint` by pak přesměrovávat všechna volání k této implementaci metody v každém programu.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Vytvořit vazbu](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
