---
title: IDebugSourceServerModule::GetSourceServerData | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0388e4a1916a16f7e429fa4f32c45ed62fdb02e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719928"
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
Načte pole informací zdrojového serveru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSourceServerData(
    ULONG* pDataByteCount,
    BYTE** ppData
);
```

```csharp
public int GetSourceServerData(
    out uint  pDataByteCount,
    out int[] ppData
);
```

## <a name="parameters"></a>Parametry
`pDataByteCount`\
[out] Počet bajtů v datovém poli.

`ppData`\
[out] Odkaz na datové pole.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro **cmodule** objekt, který zveřejňuje rozhraní [IDebugSourceServerModule.](../../../extensibility/debugger/reference/idebugsourceservermodule.md)

```cpp
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)
{
    HRESULT hr = S_OK;
    CComPtr<ISymUnmanagedReader> pSymReader;
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;

    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );
    *pDataByteCount = 0;
    *ppData = NULL;

    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );

    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)
