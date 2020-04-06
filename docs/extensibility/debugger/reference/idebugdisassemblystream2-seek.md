---
title: IDebugDisassemblyStream2::Seek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732084"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Přesune ukazatel pro čtení v datovém proudu demontáže o daný počet instrukcí vzhledem k zadané poloze.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parametry
`dwSeekStart`\
[v] Hodnota z [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) výčtu, který určuje relativní pozici zahájit proces hledání.

`pCodeContext`\
[v] [Objekt IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující kontext kódu, ke kterému je operace hledání relativní. Tento parametr se `dwSeekStart`  =  `SEEK_START_CODECONTEXT`používá pouze v případě ; v opačném případě je tento parametr ignorován a může být nulovou hodnotou.

`uCodeLocationId`\
[v] Identifikátor umístění kódu, který je vzhledem k operaci hledání. Tento parametr se `dwSeekStart`  =  `SEEK_START_CODELOCID`použije, pokud ; v opačném případě je tento parametr ignorován a lze jej nastavit na hodnotu 0. Popis identifikátoru umístění kódu naleznete v části Poznámky u metody [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`iInstructions`\
[v] Počet pokynů k přesunutí vzhledem k `dwSeekStart`poloze určené v . Tato hodnota může být záporná pro posun dozadu.

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud byla pozice hledání do bodu mimo seznam dostupných pokynů. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud hledání bylo na pozici před začátkem seznamu, pozice pro čtení je nastavena na první instrukce v seznamu. Pokud see byl na pozici po skončení seznamu, pozice pro čtení je nastavena na poslední instrukce v seznamu.

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
