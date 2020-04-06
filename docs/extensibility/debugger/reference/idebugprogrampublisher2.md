---
title: IDebugProgramPublisher2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721522"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Toto rozhraní umožňuje ladicímu modulu (DE) nebo dodavatelům vlastních portů registrovat programy pro ladění.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Visual Studio implementuje toto rozhraní zaregistrovat programy, které jsou laděny tak, aby byly viditelné pro ladění ve více procesech.

## <a name="notes-for-callers"></a>Poznámky pro volající
Volání `CoCreateInstance` funkce COM `CLSID_ProgramPublisher` s získat toto rozhraní (viz příklad). De nebo dodavatel vlastního portu používá toto rozhraní k registraci programových uzlů, které představují programy, které jsou laděny.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Zpřístupní uzel programu pro des a správce ladění relace (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Odebere uzel programu tak, aby již není k dispozici.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Zpřístupní program pro des a SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Odebere program, takže již není k dispozici.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Nastaví příznak označující, že ladicí program je k dispozici.|

## <a name="remarks"></a>Poznámky
Toto rozhraní zpřístupňuje programy a uzly programů (to znamená "publikuje" pro použití des a správce ladění relace (SDM). Chcete-li získat přístup k publikovaným programům a uzlům programů, použijte rozhraní [IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Toto je jediný způsob, jak visual studio může rozpoznat, že program je laděný.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit konkretizovat vydavatele programu a zaregistrovat uzel programu. To je převzato z [kurzu, Publikování uzel programu](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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
