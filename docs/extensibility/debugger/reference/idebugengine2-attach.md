---
title: IDebugEngine2::Připojit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731214"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Připojí ladicí modul (DE) k programu nebo programům. Volat správce ladění relace (SDM) při DE je spuštěn v procesu s SDM.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametry
`pProgram`\
[v] Pole [iDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objekty, které představují programy, které mají být připojeny k. Jedná se o přístavní programy.

`rgpProgramNodes`\
[v] Pole objektů [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) které představují uzly programu, jeden pro každý program. Programové uzly v tomto poli `pProgram`představují stejné programy jako v . Uzly programu jsou uvedeny tak, aby DE můžete identifikovat programy připojit.

`celtPrograms`\
[v] Počet programů nebo uzly programů `pProgram` `rgpProgramNodes` v polích a.

`pCallback`\
[v] [Objekt IDebugCallBackback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) který má být použit k odeslání ladicích událostí do sdm.

`dwReason`\
[v] Hodnota z [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) výčtu, který určuje důvod pro připojení těchto programů. Další informace naleznete v části Poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Existují tři důvody pro připojení k programu, a to následovně:

- `ATTACH_REASON_LAUNCH`označuje, že DE se připojuje k programu, protože uživatel spustil proces, který jej obsahuje.

- `ATTACH_REASON_USER`označuje, že uživatel výslovně požádal DE připojit k programu (nebo proces, který obsahuje program).

- `ATTACH_REASON_AUTO`označuje, že de se připojuje k určitému programu, protože již ladí jiné programy v určitém procesu. To se také nazývá automatické připojení.

  Při volání této metody DE musí odeslat tyto události v pořadí:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (pokud ještě nebylodeslán pro konkrétní instanci ladicího modulu)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Kromě toho pokud je `ATTACH_REASON_LAUNCH`důvodem pro připojení , DE potřebuje odeslat událost [IDebugEntryPointEvent2.](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

   Jakmile DE získá objekt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) odpovídající program, který je laděn, může být dotazován pro libovolné privátní rozhraní.

   Před voláním metody uzlu programu v poli `pProgram` `rgpProgramNodes`dané nebo , zosobnění, v `IDebugProgram2` případě potřeby by měla být povolena v rozhraní, které představuje uzel programu. Za normálních okolností však tento krok není nutný. Další informace naleznete v [tématu Problémy se zabezpečením](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
