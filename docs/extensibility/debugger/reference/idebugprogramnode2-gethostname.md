---
title: IDebugProgramNode2::GetHostName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 028ee16e7b9c5a30effc683494f68b2bd4eb604f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722065"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
Získá název procesu hostování programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostName (
    GETHOSTNAME_TYPE dwHostNameType,
    BSTR*            pbstrHostName
);
```

```csharp
int GetHostName (
    enum_GETHOSTNAME_TYPE dwHostNameType,
    out string            pbstrHostName
);
```

## <a name="parameters"></a>Parametry
`dwHostNameType`\
[v] Hodnota z [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) výčtu, který určuje typ názvu, který má být vrácen.

`pbstrHostName`\
[out] Vrátí název procesu hostování.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CProgram` tuto metodu pro jednoduchý objekt, který zveřejňuje rozhraní [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) Tento příklad ignoruje `dwHostNameType` parametr a vrátí pouze název programu, jak byl převzat ze základního názvu cesty k souboru modulu.

```cpp
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {
    // Check for valid argument.
    if (pbstrHostName)
    {
        char szModule[_MAX_PATH];

        // Attempt to assign to szModule the path for the file used
        // to create the calling process.
        if (GetModuleFileName(NULL, szModule, sizeof (szModule)))
        {
            // If successful then declare several char arrays
            char  szDrive[_MAX_DRIVE];
            char  szDir[_MAX_DIR];
            char  szName[_MAX_FNAME];
            char  szExt[_MAX_EXT];
            char  szFilename[_MAX_FNAME + _MAX_EXT];
            WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];

            // Break the szModule path name into components.
            _splitpath(szModule, szDrive, szDir, szName, szExt);

            // Copy the base file name szName into szFilename.
            lstrcpy(szFilename, szName);
            // Append the field extension szExt into szFilename.
            lstrcat(szFilename, szExt);

            // Convert the szFilename sequence of multibyte characters
            // to the wszFilename sequence of wide characters.
            mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);

            // Assign the wszFilename to the value at *pbstrHostName.
            *pbstrHostName = SysAllocString(wszFilename);

            return S_OK;
        }
    }

    return E_INVALIDARG;
}
```

## <a name="see-also"></a>Viz také
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
