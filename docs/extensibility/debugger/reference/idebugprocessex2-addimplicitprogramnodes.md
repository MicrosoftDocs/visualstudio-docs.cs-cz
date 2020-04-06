---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723393"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Tato metoda přidá uzel programu pro každý zadaný ladicí modul (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parametry
`guidLaunchingEngine`\
[v] De, `GUID` který má být použit ke spuštění programů (a předpokládá se, že přidat vlastní program ové uzly).

`rgguidSpecificEngines`\
[v] Pole `GUID`s des, pro které program uzly budou přidány.

`celtSpecificEngines`\
[v] Počet `GUID`s v `rgguidSpecificEngines` poli.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
- [Program Uzly](../../../extensibility/debugger/program-nodes.md) budou přidány pro `rgguidSpecificEngines`každý DE uvedené v `guidLaunchingEngine`-kromě spouštěcí motor (jak je uvedeno v ), který se předpokládá, že přidat svůj vlastní uzel programu při spuštění programu.

## <a name="see-also"></a>Viz také
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Uzly programů](../../../extensibility/debugger/program-nodes.md)
