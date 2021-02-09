---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3efe97518b0952c1207eac97fe9151f36c686f43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846553"
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
