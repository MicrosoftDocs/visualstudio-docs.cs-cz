---
description: 'IDebugProgramNode2:: getprogram Získá název programu.'
title: 'IDebugProgramNode2:: getprogram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 376054406d0c127a0bbdcd5ee0a90bc694f9cd02
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087233"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Získá název programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Parametry
`pbstrProgramName`\
mimo Vrátí název programu.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Název programu není stejný jako cesta k programu, i když název programu může být součástí této cesty.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CProgram` objekt, který implementuje rozhraní [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . `MakeBstr`Funkce přidělí kopii zadaného řetězce jako BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Viz také
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
