---
description: Získá název, popisný název nebo název souboru hostujícího procesu tohoto programu.
title: 'IDebugProgramHost2:: gethost | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4574bee7fb5a7f3ed125a73361de6fc9c3bcbfc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149519"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Získá název, popisný název nebo název souboru hostujícího procesu tohoto programu.

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
pro Hodnota z výčtu [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .

`pbstrHostName`\
mimo Vrátí požadovaný název hostitelského procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V typické implementaci této metody `dwType` je parametr ignorován a je vrácen popisný název hostitelského počítače. Další možnou implementací je předat `dwType` parametr volání metody [gethost](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) , aby se získal název.

## <a name="see-also"></a>Viz také
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
