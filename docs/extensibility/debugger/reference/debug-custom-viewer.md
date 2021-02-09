---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fa8e8d9e07510a10b1b32534f3323dab4c84a22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899106"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Struktura, která identifikuje vlastní prohlížeč nebo Vizualizér typů.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Členové
`dwID`\
ID pro odlišení více prohlížečů nebo vizualizací, které implementuje jedna `GUID` .

`bstrMenuName`\
Text, který se zobrazí v rozevírací nabídce

`bstrDescription`\
Popis vlastního prohlížeče nebo Vizualizátoru typu (musí být hodnota null, pokud se nepoužívá).

`guidLang`\
Jazyk poskytování vyhodnocovacího filtru výrazů.

`guidVendor`\
Dodavatel poskytování vyhodnocovacího filtru výrazů.

`bstrMetric`\
Metrika, pod kterou je uložen vlastní prohlížeč nebo Vizualizér typů `CLSID` .

## <a name="remarks"></a>Poznámky
Seznam této struktury je vrácen voláním metody [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (a, podle přípony, metody [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
