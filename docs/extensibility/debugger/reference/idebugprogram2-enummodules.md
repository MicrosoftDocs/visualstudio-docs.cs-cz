---
description: Načte seznam modulů, které tento program načetl a provádí.
title: 'IDebugProgram2:: Enummodules – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26016510856de44c07ca9a123553e82d0d2a79f4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149623"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Načte seznam modulů, které tento program načetl a provádí.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí objekt [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) , který obsahuje seznam modulů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Modul je knihovna DLL nebo sestavení, která je obvykle uvedena v okně ladění **modulů** .

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
