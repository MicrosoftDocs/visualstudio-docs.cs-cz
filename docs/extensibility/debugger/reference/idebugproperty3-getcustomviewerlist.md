---
title: IDebugProperty3::GetCustomViewerList | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 212f8d251232d35ee7d9cc46074a21239eea29f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721163"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Získá seznam vlastních prohlížečů přidružených k této vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celtSkip`\
[v] Počet diváků přeskočit.

`celtRequested`\
[v] Počet prohlížečů načíst (také určuje velikost `rgViewers` pole).

`rgViewers`\
[dovnitř, ven] Pole [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktur, které mají být vyplněny.

`pceltFetched`\
[out] Skutečný počet vrácených diváků.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Pro podporu vizualizérů typu tato metoda předává volání metodě [GetCustomViewerList.](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Pokud vyhodnocení výrazu také podporuje vlastní prohlížeče pro typ této vlastnosti, tato metoda můžete připojit příslušné vlastní prohlížeče do seznamu.

Podrobnosti o rozdílech mezi vizualizéry typů a vlastními prohlížeči najdete v tématu [Type Visualizer a Custom Viewer.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro **cproperty** objekt, který zveřejňuje rozhraní [IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
