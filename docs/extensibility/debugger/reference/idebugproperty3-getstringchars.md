---
title: Vlastnost IDebugProperty3::GetStringChars | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721078"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Načte řetězec přidružený k této vlastnosti a uloží jej do vyrovnávací paměti zadané uživatelem.

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
[v] Maximální počet znaků, které může obsahovat vyrovnávací paměť dodaná uživatelem.

`rgString`\
[out] Vrátí řetězec.

 [Pouze C++] `rgString` je ukazatel na vyrovnávací paměť, která přijímá znaky Unicode řetězce. Tato vyrovnávací paměť `buflen` musí mít velikost alespoň znaků (nikoli bajtů).

`pceltFetched`\
[out] Kde je vrácen počet znaků skutečně uloženy ve vyrovnávací paměti. (Může `NULL` být v jazyce C++.)

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
V jazyce C++ je třeba dbát na `buflen` to, aby vyrovnávací paměť byla alespoň dlouhé znaky Unicode. Všimněte si, že znak Unicode je 2 bajty dlouhé.

> [!NOTE]
> V jazyce C++ vrácený řetězec neobsahuje ukončující znak null. Pokud je `pceltFetched` uveden, bude určovat počet znaků v řetězci.

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
