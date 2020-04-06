---
title: IDebugProgramProvider2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721689"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Toto registrované rozhraní umožňuje správci ladění relace (SDM) získat informace o programech, které byly "publikovány" prostřednictvím rozhraní [IDebugProgramPublisher2.](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)

## <a name="syntax"></a>Syntaxe

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Ladicí modul (DE) implementuje toto rozhraní poskytnout informace o programech, které jsou laděny. Toto rozhraní je registrováno v části `metricProgramProvider`DE registru pomocí metriky , jak je popsáno v [pomocných sacích Sady SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
Volání `CoCreateInstance` funkce COM s `CLSID` poskytovatelem programu, který je získán z registru. Viz příklad.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable

|Metoda|Popis|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Získá informace o spuštěných programech, které jsou filtrovány různými způsoby.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Získá uzel programu, dané konkrétní ID procesu.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Vytvoří zpětné volání sledovat události zprostředkovatele spojené s konkrétní druhy procesů.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Vytvoří národní prostředí pro všechny prostředky specifické pro jazyk, které de potřebuje.|

## <a name="remarks"></a>Poznámky
Obvykle proces používá toto rozhraní, aby se dozvěděl o programech spuštěnéch v tomto procesu.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
