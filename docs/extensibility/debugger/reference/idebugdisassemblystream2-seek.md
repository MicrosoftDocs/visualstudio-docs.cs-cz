---
description: Přesune ukazatel na čtení ve streamu zpětného překladu a určí stanovený počet instrukcí vzhledem k zadané pozici.
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1799e2fd0fb992a2b60f57e668937a927a14e7bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170208"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Přesune ukazatel na čtení ve streamu zpětného překladu a určí stanovený počet instrukcí vzhledem k zadané pozici.

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
pro Hodnota z výčtu [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) , která určuje relativní pozici pro zahájení procesu hledání.

`pCodeContext`\
pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující kontext kódu, ke kterému je operace vyhledávání relativní. Tento parametr se používá pouze `dwSeekStart`  =  `SEEK_START_CODECONTEXT` v případě, že v opačném případě je tento parametr ignorován a může být hodnota null.

`uCodeLocationId`\
pro Identifikátor umístění kódu, ke kterému je operace vyhledávání relativní. Tento parametr se používá `dwSeekStart`  =  `SEEK_START_CODELOCID` , pokud; v opačném případě je tento parametr ignorován a lze jej nastavit na hodnotu 0. Popis identifikátoru umístění kódu naleznete v části poznámky pro metodu [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

`iInstructions`\
pro Počet instrukcí, které se mají přesunout vzhledem k pozici zadané v `dwSeekStart` . Tato hodnota může být záporná, aby se přesunuly zpět.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí, `S_FALSE` zda je pozice hledání v bodě mimo seznam dostupných instrukcí. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud je hledání na pozici před začátkem seznamu, pozice pro čtení je nastavena na první instrukci v seznamu. Pokud je vidět, že je za koncem seznamu pozice, je pozice pro čtení nastavená na poslední instrukci v seznamu.

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
