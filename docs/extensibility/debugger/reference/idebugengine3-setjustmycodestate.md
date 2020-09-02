---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730681"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Tato metoda oznamuje ladicímu stroji informace o stavu JustMyCode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
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
