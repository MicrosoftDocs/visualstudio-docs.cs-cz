---
description: Určuje pozici, od které se má začít hledání v streamu zpětného překladu.
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb097c6015b5457a0ad4808674321c410a559d2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221896"
---
# <a name="seek_start"></a>SEEK_START
Určuje pozici, od které se má začít hledání v streamu zpětného překladu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Pole
 `SEEK_START_BEGIN`\
 Začne hledání na začátku aktuálního dokumentu.

 `SEEK_START_END`\
 Začne hledání na konci aktuálního dokumentu.

 `SEEK_START_CURRENT`\
 Spustí hledání na aktuální pozici aktuálního dokumentu.

 `SEEK_START_CODECONTEXT`\
 Začne hledání v daném kontextu kódu aktuálního dokumentu.

 `SEEK_START_CODELOCID`\
 Začne hledání na daném identifikátoru umístění kódu. Identifikátory umístění kódu jsou získány voláním [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Poznámky
 Byl předán jako argument metody [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
