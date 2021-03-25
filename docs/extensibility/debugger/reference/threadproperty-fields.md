---
description: Určuje, jaké informace o vlákně se mají načíst.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81d185a80761e42e706dc3ef36da056bb37b0b1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070866"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Určuje, jaké informace o vlákně se mají načíst.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Pole
 `TPF_ID`\
 Inicializujte nebo použijte `dwThreadId` pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Inicializujte nebo použijte `dwSuspendCount` pole `THREADPROPERTIE` struktury S.

 `TPF_STATE`\
 Inicializujte nebo použijte `dwThreadState` pole `THREADPROPERTIE` struktury S.

 `TPF_PRIORITY`\
 Inicializujte nebo použijte `bstrPriority` pole `THREADPROPERTIE` struktury S.

 `TPF_NAME`\
 Inicializujte nebo použijte `bstrName` pole `THREADPROPERTIE` struktury S.

 `TPF_LOCATION`\
 Inicializujte nebo použijte `bstrLocation` pole `THREADPROPERTIE` struktury S.

 `TPF_ALLFIELDS`\
 Určuje všechna pole.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou předány jako argument metodě [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) k určení, která pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) mají být inicializována.

 Tyto hodnoty se používají také v `dwFields` členu `THREADPROPERTIES` struktury k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
