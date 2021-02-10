---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21b683e8f7797743d5ae78f932edfa5c862dbb8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967680"
---
# <a name="threadstate"></a>THREADSTATE
Určuje stav vlákna.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Pole
 `THREADSTATE_RUNNING`\
 Indikuje, že vlákno běží.

 `THREADSTATE_STOPPED`\
 Označuje, že vlákno je zastaveno z důvodu zarážky.

 `THREADSTATE_FRESH`\
 Indikuje, že vlákno bylo vytvořeno, ale ještě neběží s kódem.

 `THREADSTATE_DEAD`\
 Indikuje, že vlákno je neaktivní.

 `THREADSTATE_FROZEN`\
 Indikuje, že je vlákno zmrazeno (nelze provést žádné spuštění).

## <a name="remarks"></a>Poznámky
 Používá se pro `dwThreadState` pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
