---
title: IDebugEngine2::GetEngineID | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4071e8279c2c4ab615ff625c1bbedebfd8e64ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731078"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Získá identifikátor GUID ladicí modul (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametry
`pguidEngine`\
[out] Vrátí identifikátor GUID chyby DE.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Některé příklady typických identifikátorů GUID jsou `guidScriptEng`, `guidNativeEng`, nebo `guidSQLEng`. Nové ladicí moduly vytvoří vlastní identifikátor GUID pro identifikaci.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CEngine` tuto metodu pro jednoduchý objekt, který implementuje rozhraní [IDebugEngine2.](../../../extensibility/debugger/reference/idebugengine2.md)

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
