---
description: Získá počet vlastních prohlížečů, které mohou být pro tuto vlastnost k dispozici.
title: 'IDebugProperty3:: GetCustomViewerCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7b74c1ae5a29b785de42295af3260f17655986c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064680"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Získá počet vlastních prohlížečů, které mohou být pro tuto vlastnost k dispozici.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
mimo Počet vlastních prohlížečů dostupných pro tuto vlastnost.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Aby bylo možné podporovat typy vizualizací, tato metoda přepošle volání metody [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Pokud vyhodnocení výrazu také podporuje vlastní diváky pro tento typ vlastnosti, tato metoda přidá počet vlastních prohlížečů do vrácené hodnoty.

Podrobné informace o rozdílech mezi typy vizualizace a vlastními prohlížeči naleznete v tématu [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **CProperty** , který zpřístupňuje rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
