---
description: Informuje ladicí stroj (DE), že zadaný program byl neobvyklým ukončen a že DE by měl vyčistit všechny odkazy na program a odeslat událost zničení programu.
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0a58dd5893c3235ded9c7eeb5f5d47e3ddcb380
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093844"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informuje ladicí stroj (DE), že zadaný program byl neobvyklým ukončen a že DE by měl vyčistit všechny odkazy na program a odeslat událost zničení programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parametry
`pProgram`\
pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, který byl neobvyklým zakončením.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po zavolání této metody zruší následně událost [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) zpátky do Správce ladění relace (SDM).

 Tato metoda není implementována (vrátí `E_NOTIMPL` ), pokud de běží ve stejném procesu jako program, který se právě ladí. Tato metoda je implementována pouze v případě, že je DE spuštěna ve stejném procesu jako model SDM.

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
