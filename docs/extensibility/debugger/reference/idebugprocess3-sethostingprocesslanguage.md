---
description: Tato metoda nastaví jazyk, pod kterým bude proces hostovaný.
title: 'IDebugProcess3:: SetHostingProcessLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d2a95a5f8181b7b58198a8a56b7fb0037ef0bc1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150117"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Tato metoda nastaví jazyk, pod kterým bude proces hostovaný. Tento jazyk je pak možné použít ladicím modulem (DE) k načtení příslušného vyhodnocovacího filtru výrazů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Parametry
`guidLang`\
[in] `GUID` jazyk, který by měl DE použít. Určete `GUID_NULL` (C++) nebo `Guid.Empty` (C#), aby měl de použít výchozí jazyk.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) se dá použít k načtení aktuálního nastavení jazyka.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
