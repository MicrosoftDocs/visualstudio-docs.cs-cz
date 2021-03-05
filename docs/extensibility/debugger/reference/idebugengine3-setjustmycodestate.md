---
description: Tato metoda oznamuje ladicímu stroji informace o stavu JustMyCode.
title: 'IDebugEngine3:: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153700"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Tato metoda oznamuje ladicímu stroji informace o stavu JustMyCode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametry
`fUpdate`\
pro Nenulová ( `TRUE` ) pro aktualizaci aktuálních informací, nula ( `FALSE` ) pro resetování všech informací (ignoruje vše dříve nastavené).

`dwModules`\
pro Počet informačních struktur v `rgJMCSpec.`

`rgJMCSpec`\
pro Pole [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) struktury, které se mají použít.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 JustMyCode je koncept ladění pouze kódu, který patří uživateli a ignoruje všechny zprostředkující kódy, jako je například systémový kód, i když je zdrojový kód k dispozici pro tento systémový kód.

## <a name="see-also"></a>Viz také
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
