---
description: Toto rozhraní představuje počáteční pozici instrukce kódu.
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d1fcf5ed3b40d0fafdc8ecf9a88c7000f01d5d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088351"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Toto rozhraní představuje počáteční pozici instrukce kódu. Pro většinu architektur za běhu v současné době je možné kontext kódu představit jako adresu v datovém proudu spuštění programu.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní, aby se spojila pozice instrukce kódu na pozici dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody v mnoha rozhraních vrací toto rozhraní, většinou [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Používá se také rozsáhlě s rozhraním [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) i v informacích o rozlišení zarážek.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v rozhraní [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Získá kontext dokumentu, který odpovídá aktivnímu kontextu kódu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Získá informace o jazyce pro tento kontext kódu.|

## <a name="remarks"></a>Poznámky
 Klíčovým rozdílem mezi `IDebugCodeContext2` rozhraním a rozhraním [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) je, že `IDebugCodeContext2` je vždy zarovnán s pokyny. To znamená, že `IDebugCodeContext2` se vždy odkazuje na začátek instrukce, zatímco `IDebugMemoryContext2` může ukazovat na libovolný bajt paměti v architektuře run-time. `IDebugCodeContext2` se zvětšuje podle pokynů, nikoli podle základní velikosti úložiště (obvykle Byte).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
