---
description: Načte řetězec přidružený k této vlastnosti a uloží ji do uživatelem zadané vyrovnávací paměti.
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3b220fa02809015d1fa699c5e9eb5edac8cf2f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166681"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Načte řetězec přidružený k této vlastnosti a uloží ji do uživatelem zadané vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parametry
`buflen`\
pro Maximální počet znaků, které může obsahovat uživatelsky zadaná vyrovnávací paměť.

`rgString`\
mimo Vrátí řetězec.

 [Pouze C++] `rgString` je ukazatel na vyrovnávací paměť, která přijímá znaky Unicode řetězce. Velikost této vyrovnávací paměti musí být minimálně `buflen` znaků (ne bajtů).

`pceltFetched`\
mimo Kde je vrácen počet znaků skutečně uložených ve vyrovnávací paměti. (Může být `NULL` v jazyce C++.)

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
V jazyce C++ je třeba dbát na to, aby vyrovnávací paměť měla `buflen` délku alespoň znaků Unicode. Všimněte si, že znak Unicode má délku 2 bajty.

> [!NOTE]
> V jazyce C++ vrácený řetězec nezahrnuje ukončující znak null. Je-li zadán, `pceltFetched` určí počet znaků v řetězci.

## <a name="example"></a>Příklad

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Viz také
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
