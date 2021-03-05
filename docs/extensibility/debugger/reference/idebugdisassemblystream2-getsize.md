---
description: Získá velikost v pokynech tohoto streamu zpětného překladu.
title: 'IDebugDisassemblyStream2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94207c8e14306049068e838971aa778290de2ba6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154363"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Získá velikost v pokynech tohoto streamu zpětného překladu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parametry
`pnSize`\
mimo Vrátí velikost v instrukcích.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnotu vrácenou touto metodou lze použít k přidělení pole [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, které jsou poté předány metodě [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Oprávnění](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
