---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: Výčet INTERCEPT_EXCEPTION_ACTION určuje, jaká akce má být provedena při zachytávání výjimek v ladění sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5e1038ac2515198d5eb20b66f346f7a6798c25a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852788"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Určuje, jaké akce se mají provést při zachytávání výjimek.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Parametry

`IEA_INTERCEPT`\
Povoluje zachycení aktuální výjimky. Toto je jediná hodnota podporovaná v současnosti a musí se zadat.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou předány do metody [InterceptCurrentException –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
