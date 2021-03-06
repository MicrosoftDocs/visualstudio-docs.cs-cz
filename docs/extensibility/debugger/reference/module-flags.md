---
description: Slouží k popisu modulu.
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e671b3e578a78665a6a816582e0290119f77ea58
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225471"
---
# <a name="module_flags"></a>MODULE_FLAGS
Slouží k popisu modulu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Pole
 `MODULE_FLAG_NONE`\
 Určuje žádný modul.

 `MODULE_FLAG_SYSTEM`\
 Určuje systémový modul.

 `MODULE_FLAG_SYMBOLS`\
 Určuje modul symbolů.

 `MODULE_FLAG_64BIT`\
 Určuje 64 modul.

 `MODULE_FLAG_OPTIMIZED`\
 Určuje, že je modul optimalizovaný. Tento stav se projeví v okně **moduly** .

 `MODULE_FLAG_UNOPTIMIZED`\
 Určuje, že modul není optimalizovaný. Tento stav se projeví v okně **moduly** . Toto je výchozí stav.

## <a name="remarks"></a>Poznámky
 Používá se pro `m_dwModuleFlags` člena [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.

 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
