---
description: Tato metoda přidá uzel programu pro každý zadaný ladicí stroj (DE).
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3a4c6446c2106d79dd14fc0378fc848eac3df18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159988"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Tato metoda přidá uzel programu pro každý zadaný ladicí stroj (DE).

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
pro A `GUID` , který se má použít ke spuštění programů (a předpokládá se, že se mají přidat vlastní uzly programu).

`rgguidSpecificEngines`\
pro Pole `GUID` s des, pro které budou přidány uzly programu.

`celtSpecificEngines`\
pro Počet `GUID` s v poli `rgguidSpecificEngines` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
- [Uzly programu](../../../extensibility/debugger/program-nodes.md) budou přidány pro každý z níže uvedených v `rgguidSpecificEngines` – bez spouštěcího modulu (jak je uvedeno v části `guidLaunchingEngine` ), což předpokládá, že při spuštění programu dojde k přidání vlastního uzlu programu.

## <a name="see-also"></a>Viz také
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Uzly programů](../../../extensibility/debugger/program-nodes.md)
