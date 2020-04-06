---
title: IDebugDisassemblyStream2::Číst | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732093"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Přečte pokyny počínaje aktuální polohou v datovém proudu demontáže.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parametry
`dwInstructions`\
[v] Počet pokynů k demontáži. Tato hodnota je také maximální `prgDisassembly` délka pole.

`dwFields`\
[v] Kombinace příznaků z [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) výčtu, které `prgDisassembly` označují, která pole mají být vyplněna.

`pdwInstructionsRead`\
[out] Vrátí počet skutečně rozebránin instrukcí.

`prgDisassembly`\
[out] Pole [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, která je vyplněna s rozložený kód, jedna struktura na rozložené instrukce. Délka tohoto pole je dána `dwInstructions` parametrem.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Maximální počet instrukcí, které jsou k dispozici v aktuálním oboru lze získat voláním [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) metoda.

 Aktuální pozici, kde je číst další instrukce z lze změnit voláním [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metoda.

 Příznak `DSF_OPERANDS_SYMBOLS` lze přidat do `DSF_OPERANDS` příznaku `dwFields` v parametru označující, že názvy symbolů by měly být použity při rozebrání pokyny.

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
