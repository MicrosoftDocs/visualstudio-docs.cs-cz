---
description: Toto rozhraní umožňuje modulům ladění (DE) nebo vlastním dodavatelům portů registrovat programy pro ladění.
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c51fac369ed91f00c91482dd7069362d758b7346
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065096"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Toto rozhraní umožňuje modulům ladění (DE) nebo vlastním dodavatelům portů registrovat programy pro ladění.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Visual Studio implementuje toto rozhraní k registraci programů, které jsou laděny, aby je bylo možné zobrazit pro ladění v rámci více procesů.

## <a name="notes-for-callers"></a>Poznámky pro volající
Volání funkce modelu COM `CoCreateInstance` s `CLSID_ProgramPublisher` cílem získat toto rozhraní (viz příklad). Dodavatel DE nebo vlastní port používá toto rozhraní k registraci uzlů programu, které reprezentují laděné programy.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Zpřístupňuje uzel programu pro algoritmus DEs a správce ladění relace (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Odebere uzel programu, aby už není dostupný.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Vytvoří program k dispozici pro algoritmus DEs a SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Odebere program, aby už není dostupný.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Nastaví příznak označující, že je k dispozici ladicí program.|

## <a name="remarks"></a>Poznámky
Toto rozhraní zpřístupňuje programy a uzly programu (tj. "publikace") pro použití algoritmem DEs a správce ladění relace (SDM). Chcete-li získat přístup k publikovaným programům a uzlům programu, použijte rozhraní [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Toto je jediný způsob, jak může Visual Studio rozpoznat, že je program laděný.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit instanci vydavatele programu a zaregistrovat uzel programu. Tato akce je pořízena z kurzu [publikování uzlu programu](/previous-versions/bb161795(v=vs.90)).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
