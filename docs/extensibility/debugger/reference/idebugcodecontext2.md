---
title: IDebugCodeContext2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734212"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Toto rozhraní představuje počáteční pozici instrukce kódu. Pro většinu architektur za běhu dnes kontextu kódu lze považovat za adresu v proudu spuštění programu.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní tak, aby se vztahovalo pozici instrukce kódu k pozici dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody na mnoha rozhraních vrátit toto rozhraní, většinou [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Používá se také značně s [rozhraním IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) stejně jako v informacích o rozlišení zarážky.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraní [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Získá kontext dokumentu, který odpovídá kontextu aktivního kódu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Získá informace o jazyce pro tento kontext kódu.|

## <a name="remarks"></a>Poznámky
 Klíčovým rozdílem `IDebugCodeContext2` mezi rozhraním a rozhraním [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) je, že `IDebugCodeContext2` je vždy zarovnán instrukcemi. To znamená, `IDebugCodeContext2` že je vždy ukazuje na začátek `IDebugMemoryContext2` instrukce, vzhledem k tomu, může překážet na jakýkoli bajt paměti v architektuře běhu. `IDebugCodeContext2`je se zvětšuje pokyny spíše než základní velikost úložiště (obvykle bajt).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
