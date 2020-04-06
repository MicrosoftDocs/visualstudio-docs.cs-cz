---
title: IDebugEngine3::SetJustMyCodeState | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730681"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Tato metoda informuje ladicí stroj o informacích o stavu JustMyCode.

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
[v] Nenulová`TRUE`( ) pro aktualizaci aktuálních informací, nula (`FALSE`) pro resetování všech informací (ignorování všeho, co bylo dříve nastaveno).

`dwModules`\
[v] Počet informačních struktur`rgJMCSpec.`

`rgJMCSpec`\
[v] Pole [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) struktur, které chcete použít.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 JustMyCode je koncept ladění pouze kód, který patří uživateli a ignoruje všechny zprostředkující kód, jako je například systémový kód – i v případě, že zdrojový kód je k dispozici pro tento systémový kód.

## <a name="see-also"></a>Viz také
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
