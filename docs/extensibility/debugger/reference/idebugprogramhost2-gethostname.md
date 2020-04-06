---
title: IDebugProgramHost2::GetHostName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722227"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Získá název, popisný název nebo název souboru hostitelského procesu tohoto programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parametry
`dwType`\
[v] Hodnota z [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) výčtu.

`pbstrHostName`\
[out] Vrátí požadovaný název procesu hostování.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V typické implementaci této metody `dwType` je parametr ignorován a je vrácen popisný název hostitelského počítače. Další možnou `dwType` implementací je předat parametr volání metody [GetHostName,](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) aby získal název.

## <a name="see-also"></a>Viz také
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
